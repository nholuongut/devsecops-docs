---
description: Building images with Bitbucket Pipelines
---

# Build a Docker image

When building Docker images, use pipelines as much as possible. This example assumes that you are using the default Atlassian builder image in [this example](https://hub.docker.com/r/atlassian/default-image/).&#x20;

To publish a new image to AWS Elastic Container Registry (ECR), for example, use the following sample code to publish a new image when the repo is tagged:&#x20;

```yaml
pipelines:
  tags:
    '**': 
    - step: 
        name: Publish New Image
        # oidc: true indicates that OIDC authentication has been enabled.
        oidc: true  
        script:
        - docker build . -t $BITBUCKET_REPO_SLUG
        - pipe: atlassian/aws-ecr-push-image:1.6.2
          variables:
            AWS_DEFAULT_REGION: us-east-1
            AWS_OIDC_ROLE_ARN: $AWS_OIDC_ROLE_ARN
            IMAGE_NAME: $BITBUCKET_REPO_SLUG
            TAGS: "latest $BITBUCKET_TAG"           
```

{% hint style="info" %}
**NOTE**: OIDC is `true` when [OIDC Authentication is enabled](configure-bitbucket.md).&#x20;
{% endhint %}

