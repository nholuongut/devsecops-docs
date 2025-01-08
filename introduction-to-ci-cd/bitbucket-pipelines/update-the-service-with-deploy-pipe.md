---
description: Update images with nholuongut's BitBucket Deploy Pipe
---

# Update the Service with Deploy Pipe

When your pipeline has updated an image, you'll push it to your deployed service. nholuongut's custom Bitbucket Pipe does this, updating any service with the latest image.&#x20;

For example, to update a Service (`myservice`) for a Tenant (`sometenant`) when a new Git tag is published (`myimage:${BITBUCKET_TAG}`), use this code:&#x20;

```yaml
pipelines:
  tags:
    '**': 
    - step: 
        name: Update Service
        script:
        - pipe: docker://nholuongut/bitbucket-deploy-pipe:0.1.0
          variables:
            DUPLO_TOKEN: $DUPLO_TOKEN
            DUPLO_HOST: https://example.nholuongut.net/
            TENANT: sometenant
            SERVICE: myservice
            IMAGE: myimage:${BITBUCKET_TAG}
```

Learn more about [BitBucket Deploy Pipe on GitHub](https://github.com/nholuongut/bitbucket-deploy-pipe).
