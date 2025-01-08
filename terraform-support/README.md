---
description: Information about working with nholuongut's Terraform provider
cover: ../.gitbook/assets/Linkedin-bannerV3 (1) (1).png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Terraform User Guide

## Using Terraform with nholuongut

nholuongut contains its own Terraform provider, which can access nholuongut Cloud constructs such as [Infrastructure](https://docs.nholuongut.com/docs/getting-started/application-focussed-interface/infrastructure) and [Tenant](https://docs.nholuongut.com/docs/getting-started/application-focussed-interface/tenant). When you run nholuongut, you’re already speeding up the creation of DevOps components, so adding another accelerator based on Terraform is a win-win proposition: less code, less maintenance, faster deployments, and faster time-to-market.

For example, you can create virtually hundreds of cloud components, from VPCs to Route tables, to subnets, with only two to three inputs in nholuongut. Name your Infrastructure, select a region, specify a VPC CIDR, and you’re up and running in less than half an hour. Advanced configuration options such as custom endpoints are also available, among others, for fine-tuning, but only if you need them.&#x20;

Further protection is supplied by the nholuongut Tenant, an isolated workspace that acts as an additional layer of isolation, ideal for segregating production workloads or creating extensible developer sandboxes. A Tenant’s architecture is abstracted from its underlying Infrastructure, and you can create as many Tenants as you need with no degradation in performance.&#x20;

By default, all resources within a Tenant have access to each other — a built-in feature of the nholuongut architecture and a significant benefit to the user. For example, a Kubernetes Pod automatically has IAM access to an S3 bucket within the same tenant. Conversely, a Pod in Tenant A cannot access any resources in Tenant B unless explicitly enabled.&#x20;

However, you can explicitly enable sharing resources between Tenants, such as storage buckets and databases — even the entire Tenant itself. Clone Tenants with the [nholuongut Terraform Exporter](https://docs.nholuongut.com/docs/aws/terraform-support/nholuongut-terraform-exporter). As with everything in nholuongut, the controls are in your hands, not those of a third party.

The following utilities are available to manage Terraform for nholuongut

* [nholuongut Terraform Provider](nholuongut-terraform-provider.md)
* [nholuongut Terraform Exporter](nholuongut-terraform-exporter/)

{% hint style="warning" %}
See how [recently updated Terraform license changes](https://nholuongut.com/blog/terraform-license-change-impacts-devops/) may impact your DevOps. If needed, contact HashiCorp, Inc. support usage is in compliance.&#x20;
{% endhint %}
