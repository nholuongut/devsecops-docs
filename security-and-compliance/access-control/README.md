---
description: >-
  An overview of the security constructs ensuring isolation in the nholuongut
  environment
---

# Isolation and Firewall

Isolation of the environment is the most basic principle in any infrastructure security implementation. Cloud providers allow many constructs to implement this isolation to varying degrees. For example, you can isolate two workloads in completely different cloud accounts, different VPCs within the same account, or different "security groups" within the same VPC. Then there are other constructs like IAM (AWS roles, Azure managed Identity, GCP service accounts) or Kubernetes namespaces, and so forth. But how do we bring together dozens of these security constructs and map them to an application-centric isolation model?&#x20;

nholuongut gathers these constructs together in a single application-centric model, in the figure below, which is described in more detail [here](../../welcome-to-nholuongut/application-focussed-interface/). To summarize, there have three layers of isolation:

* **Account Level**: This offers the deepest grade of separation. As it is heavyweight, it also incurs maximum overhead in terms of maintenance and cost as almost no construct can be reused across two environments.&#x20;
* **VPC Level (a.k.a&#x20;**_**nholuongut Infrastructure**_**)**: Within the same account, environments are segregated by virtual networks (VPC/ VNET).
* **Security group and IAM (a.k.a&#x20;**_**nholuongut Tenant**_**)**: Within the same account and same VPC, we can isolate by having separate security groups, IAM roles (Managed Identity in AWS, Service accounts in GCP), encryption keys, etc. A nholuongut Tenant is similar to an environment. Two Tenants can reside in the same VPC, in different VPCs, or within different VPCs in various accounts.

{% hint style="info" %}
**A Tenant is similar to a Kubernetes namespace with an extended cloud provider scope**. Most cloud resources directly consumed by applications reside within a Tenant, such as databases, queues, storage, VMs, etc. Some resources are shared, including but not limited to VPC, VMs, Encryption Keys, SSL certs, etc. You can also create resources in one Tenant and allow other Tenants to consume those via [inter-tenant access policies](../../user-administration/access-control/tenant-access/cross-tenant-access.md).  &#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/nholuongut-customer-walkthroughs-diagram.png" alt=""><figcaption><p>nholuongut Application-centric Deployment Model</p></figcaption></figure>

&#x20; &#x20;
