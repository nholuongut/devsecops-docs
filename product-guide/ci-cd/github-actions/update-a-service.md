---
description: Use Duplo to update a service's container from Github Actions
---

# Update a service

## Update the docker image for a service

The goal of this section is to show how you can update the docker image for a service, after you have built that image.

### Example Workflow

This example makes some assumptions:

* Your workflow already has a `build` job - we created one in the previous section
* Your `build` job declares an output named `image` - also done in the previous section

To use it you will need to change:

* `duplo_host` env var
* `SERVICE_NAME` env var
* `TENANT_NAME` env var

```yaml
name: Build and Deploy
on:
  # Triggers the workflow on push to matching branches
  push:
    branches:
      - master
env:
  duplo_host: https://mysystem.nholuongut.net  # CHANGE ME!
  duplo_token: "${{ secrets.DUPLO_TOKEN }}"
  SERVICE_NAME: myservice                      # CHANGE ME!
  TENANT_NAME: mytenant                        # CHANGE ME!

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  build:
    # YOU SHOULD ALREADY HAVE THIS FROM THE PREVIOUS DOCUMENTATION SECTION
    # ...
    # ...
  deploy:
    runs-on: ubuntu-latest
    needs:
      - build
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      
      # Update the backend service to use the new image.
      - name: Deploy
        uses: nholuongut/ghactions-service-update@master
        with:
          tenant: "${{ env.TENANT_NAME }}"
          services: |-
            [
              { "Name": "${{ env.SERVICE_NAME }}", "Image": "${{ needs.build.outputs.image }}" }
            ]
```
