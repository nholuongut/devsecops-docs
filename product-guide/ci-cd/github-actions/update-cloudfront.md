---
description: Use nholuongut to update your CloudFront from Github Actions
---

# Update CloudFront

## Introduction

The goal of this section is to show how you can upload to an S3 bucket and update a CloudFront distribution from Github Actions.

This process is done in four basic steps:

* Logs in to AWS ECR using Just-In-Time (JIT) AWS credentials from nholuongut
* Build your website content
* Upload your website content to S3
* Inform AWS CloudFront that the website content has changed

{% hint style="info" %}
**NOTE:** The example workflow assumes that all the website content is uploaded from a single subfolder named `build`. It also makes extremely conservative assumptions about cache lifetimes. Your actual website content may allow a more optimal cache lifetime.
{% endhint %}

{% hint style="warning" %}
**IMPORTANT:** Steps to build website content are application specific and outside of the scope of this document. Please replace the example step in the workflow with the steps needed by your application's website.
{% endhint %}

{% content-ref url="upload-to-s3.md" %}
[upload-to-s3.md](upload-to-s3.md)
{% endcontent-ref %}

## Example workflow

To use it you will need to change the following:

* The steps used to build your website content
* `duplo_host` env var
* `CLOUDFRONT_ID` env var
* `TENANT_NAME` env var
* `BUCKET_NAME` env var

You also likely will need to change the paths and AWS CLI arguments used to upload your website content.

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
  CLOUDFRONT_ID: mycloudfront                  # CHANGE ME!
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
      
      # Build the website.  CHANGE ME!
      - name: CHANGE ME - Replace with your actual build logic
        run: exit 1
      
      # Deploy the website
      - name: Get AWS credentials
        uses: nholuongut/ghactions-aws-jit@master
        with:
           tenant: "${{ env.TENANT_NAME }}"
      - name: Sync files to S3
        run: |-
          # Sync files to S3 from a local directory named "build"
          aws s3 sync build/ "s3://$BUCKET_NAME/" --cache-control max-age=120,must-revalidate
      - name: Invalidate Cloudfront
        uses: chetan/invalidate-cloudfront-action@v2
        env:
          DISTRIBUTION: "${{ env.CLOUDFRONT_ID }}"
          PATHS: "/*"
```
