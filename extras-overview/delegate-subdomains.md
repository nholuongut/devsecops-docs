---
description: How to delegate subdomains to another Cloud Provider
---

# Delegate Subdomains

When managing a domain, such as `example.com`, you may want to delegate control of specific subdomains to different cloud platforms. The guide will help you go through the steps how to delegate subdomain from a Cloud Provider to a hosted zone in AWS and GCP.

Lets assume you have `example.com` registed in a DNS Provider such as GoDaddy or CloudFlare, and we want to be able to delegate:

* `aws.example.com`. to your AWS account
* `gcp.example.com`. to your GCP account

### Delegate subdomains to AWS

For DNS management, AWS offers Amazon Route 53. Here are the steps you need to take:

1. Create a hosted zone for `aws.example.com` in Route 53.
2. Note down the nameserver (NS) records that Route 53 assigns to your new hosted zone
3. To delegate the DNS control, you need to update the DNS settings of your primary domain `example.com` in the DNS Provider.
4. Go to where `example.com` is hosted, and add NS records for `aws.example.com`, pointing to the nameservers you noted from AWS Route 53.

This configuration delegates the management of `aws.example.com` to AWS.

### Delegate subdomains to GCP

1. Create a managed zone for `gcp.example.com` in Google Cloud DNS.
2. Note down the nameserver (NS) records assigned to the managed zone.
3. Update the DNS settings for your primary domain `example.com` in your DNS Provider to delegate GCP:
4. Go to where `example.com` is hosted. and add NS records for `gcp.example.com`, pointing to the nameservers noted from Google Cloud DNS.

This configures the delegation of `gcp.example.com` to GCP.
