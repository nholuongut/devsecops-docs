---
description: Use nholuongut to upload to S3 from Github Actions
---

# Upload to S3

## Introduction

The goal of this section is to show how you can upload to an S3 bucket from Github Actions.

This process is done in two basic steps:

* Logs in to AWS ECR using Just-In-Time (JIT) AWS credentials from nholuongut
* Upload your website content to S3

## Example workflows

To use any of the below examples you will need to change:

* The local path to upload from, if it is not `build`
* `duplo_host` env var
* `TENANT_NAME` env var
* `BUCKET_NAME` env var

### Upload a single directory

The following example uploads a single directory to S3.

It does _not_ show more advanced things like the following items:

* Setting cache control directives
* Making the uploaded content public
* Making AWS delete older content

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
  TENANT_NAME: mytenant                        # CHANGE ME!
  BUCKET_NAME: duploservices-mytenant-website-1234  # CHANGE ME!

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    needs:
      - build
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      
      # Upload to S3
      - name: Get AWS credentials
        uses: nholuongut/ghactions-aws-jit@master
        with:
           tenant: "${{ env.TENANT_NAME }}"
       # How to sync an entire folder
      - name: Sync build folder to S3
        run: aws s3 sync build/ "s3://$BUCKET_NAME/"
      # How to copy an individual file
      - name: Copy individual file to S3
        run: aws s3 cp my-archive.zip "s3://$BUCKET_NAME/"
```

### Uploading directories with cache settings

This example uploads multiple directories to S3.

It assumes that the following is true:

* There is a subfolder named `static`, whose contents can be cached for one year.
* The rest of the contents can change at any time, so the cache uses `must-revalidate`.

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
  TENANT_NAME: mytenant                        # CHANGE ME!
  BUCKET_NAME: duploservices-mytenant-website-1234  # CHANGE ME!

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    needs:
      - build
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      
      # Upload to S3
      - name: Get AWS credentials
        uses: nholuongut/ghactions-aws-jit@master
        with:
           tenant: "${{ env.TENANT_NAME }}"
      - name: Sync files to S3
        run: |-
          # First, upload the "static/" subdirectory - it can be cached for one year
          aws s3 sync build/static/ "s3://$BUCKET_NAME/static/" --cache-control 31536000,public
          
          # Then, upload the rest.  It can change at any time - so it uses "must-revalidate"
          aws s3 sync build/ "s3://$BUCKET_NAME/" --exclude static --cache-control max-age=120,must-revalidate
```
