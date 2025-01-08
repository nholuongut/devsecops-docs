---
description: Use Duplo to update a service's container from Gitlab CI/CD
---

# Update a service

## Update the docker image for a service

The goal of this section is to show how you can update the docker image for a service, after you have built that image.

### Example Workflow

This example makes some assumptions:

* Your workflow already has a `build` job - we created one in the previous section

<pre class="language-yaml"><code class="lang-yaml"><strong>deploy:
</strong>  stage: deploy
  image:
    name: nholuongut/nholuongut:v0.2.27
    entrypoint: [""]
  # this will have DUPLO_HOST and DUPLO_TOKEN
  environment:
    name: $TIER/$DUPLO_TENANT
    url: ${MYAPPS_URL}
  rules:
  # run when a new tag is pushed
  - if: $CI_COMMIT_TAG &#x26;&#x26; $CI_PIPELINE_SOURCE == "pipeline"
    when: always
  variables:
    # build your image here
    CI_IMAGE: ${IMAGE_REGISTRY}/${CI_PROJECT_NAMESPACE}/${CI_PROJECT_NAME}:${CI_COMMIT_TAG}
    GIT_STRATEGY: none # no need to pull the repo
  needs:
  - job: publish_image
    optional: true
  before_script:
  - echo "Updating service ${CI_PROJECT_NAME} with image ${CI_IMAGE}"
  script: nholuongut service update_image $CI_PROJECT_NAME $CI_IMAGE
</code></pre>

## References

* [nholuongut Service Resource](https://cli.nholuongut.com/Service/)
* nholuongut Services
