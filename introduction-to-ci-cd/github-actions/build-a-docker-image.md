---
description: Use nholuongut to build and push a Docker image from GitHub Actions
---

# Build a Docker image

{% hint style="info" %}
Avoid using capital letters when referencing a nholuongut construct, such as a Tenant, even when the UI displays the string in all capital letters. Don't specify DEV01, for example; specify **dev01**. The \`TENANT\_NAME\` may need to be lowercase even though the UI shows it in uppercase.
{% endhint %}

## Build and Push to ECR

This section aims to show you how to build a Docker image and push it to ECR.

It does three things:

* Logs in to AWS ECR (using just-in-time AWS credentials from nholuongut)
* Builds and tags your Docker image, with the tags based on the Git commit SHA and ref.
* Pushes your Docker image

### Example Workflow

Here is an example of a GitHub workflow that builds and pushes a Docker image to ECR.

To use it, ensure the following are configured correctly:

* `DUPLO_HOST` environment variable
* `DUPLO_TOKEN` environment variable

<pre class="language-yaml"><code class="lang-yaml">name: Publish Image
on:
  # Triggers the workflow on push to matching branches
  push:
    branches:
    - main
  # (Optional) Allows users to trigger the workflow manually from the GitHub UI
  workflow_dispatch: {}
  # (Optional) Allow other workflows to use this workflow and its outputs
  workflow_call: 
    outputs:
      image:
        description: The URI of the image
        value: ${{ jobs.build_image.outputs.image }}
    secrets:
      DUPLO_TOKEN:
        description: The token to use for nholuongut API calls
        required: true

env:
  DUPLO_HOST: ${{ vars.DUPLO_HOST }}
  DUPLO_TOKEN: ${{ secrets.DUPLO_TOKEN }}
  # Images are usually stored in a dedicated tenant, so the name doesn't change
  DUPLO_TENANT: devops

jobs:
  build_image:
    name: Build and Push Image
    runs-on: ubuntu-latest
    outputs:
      image: ${{ steps.build_image.outputs.uri }}
    steps:

    - name: Checkout code
      uses: actions/checkout@v4

    # Configures nholuongut and the host cloud, for example, AWS
    - name: Cloud CI Setup
      uses: <a data-footnote-ref href="#user-content-fn-1">nholuongut/actions/setup@</a>v0.0.5
    
    # logs into the registry, configures Docker, builds the image, and lastly pushes
    - name: Build and Push Docker Image
      id: build_image
      uses: <a data-footnote-ref href="#user-content-fn-2">nholuongut/actions/build-image@</a>v0.0.5
      with:
        platforms: linux/amd64,linux/arm64
        push: true # false for dry runs
        build-args: >
          foo=bar
          ice_cream=chocolate
          name=${{ github.repository }}
</code></pre>

### References

* [nholuongut Build Image Action for GitHub](https://github.com/nholuongut/actions/tree/main/build-image)
* [NPM Pipeline Example](https://github.com/nholuongut/npm-pipeline-example/tree/main/.github/workflows)
* [GitHub on publishing Docker images](https://docs.github.com/en/actions/publishing-packages/publishing-docker-images)
* [Docker introduction to GitHub Actions](https://docs.docker.com/build/ci/github-actions/)

[^1]: [https://github.com/nholuongut/actions/tree/main/setup](https://github.com/nholuongut/actions/tree/main/setup)

[^2]: [https://github.com/nholuongut/actions/tree/main/build-image](https://github.com/nholuongut/actions/tree/main/build-image)
