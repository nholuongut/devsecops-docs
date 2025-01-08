---
description: The nholuongut Tenant as an IAM boundary
---

# IAM

Access to PaaS services by cloud providers is not network policy-based but based on the provider's IAM framework. For example, AWS uses IAM policies, Azure uses managed identities and GCP uses service accounts. Similarly, in a Kubernetes cluster,  service accounts are used.

nholuongut Tenant is an IAM boundary. Any PaaS resource within a Tenant is automatically accessed by the compute workload using IAM. For example:

* In AWS, each Tenant is an IAM role and computing resource, as VMs, Lambda functions, EMR, Airflow Jobs, etc are given the IAM role which in turn is configured to have access to all PAAs services in that Tenant like  S3 buckets, DynamoDB tables, secrets manager, SSM parameter, SQS queues etc.
* In Azure, each Tenant is a managed identity and computing resource, as VMs, Lambda functions, etc are attached to this managed identity which in turn is configured to have access to all PaaS services in that Tenant like Azure storage, Keyvault, etc.&#x20;
* In GCP, each Tenant is a service account and computing resource, as VMs, functions, etc are attached to this service account which in turn is configured to have access to all PaaS services in that Tenant like cloud storage, Pub/Sub, etc.
