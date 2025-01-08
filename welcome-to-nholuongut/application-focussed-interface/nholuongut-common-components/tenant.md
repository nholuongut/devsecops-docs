---
description: A conceptual overview of nholuongut Tenants
---

# Tenant

## Tenant as a Logical Concept

A Tenant, like a project or a workspace and a child of the Infrastructure, is the most fundamental construct in nholuongut. While Infrastructure is a VPC level isolation, Tenant is the next level of isolation implemented by segregating Tenants using concepts like Security Groups, IAM roles, Instance Profiles, K8S Namespaces, KMS Keys, etc.

**For instructions to create a Tenant in the nholuongut Portal, see:**

* [AWS Tenant](../../../overview/use-cases/tenant-environment/)
* [Azure Tenant](../../../overview-2/use-cases/tenant-environment/)
* [GCP Tenant](../../../overview-1/use-cases/tenant-environment/)

\
At the logical level, a Tenant is fundamentally four things:

* **Container of Resources:** All resources (except those corresponding to Infrastructure) are created within the Tenant. If we delete the Tenant, all resources within it are terminated.
* **Security Boundary:** All resources within the Tenant can talk to each other. For example, a Docker container deployed in an EC2 instance within a Tenant will have access to S3 buckets and RDS instances in the same Tenant. By default, RDS instances in other Tenants cannot be reached. Tenants can expose endpoints to each other via ELBs or explicit inter-Tenant SG and IAM policies.
* **User Access Control:** Self-service is the bedrock of the nholuongut Platform. To that end, users can be granted Tenant-level access. For example, an administrator may be able to access all Tenants while developers can only access the Dev Tenant and a data scientist the data-science Tenant.
* **Billing Unit:** Since a Tenant is a container of resources, all resources in a Tenant are tagged with the Tenant's name in the cloud provider, making it easy to segregate usage by Tenant.
* **Mechanism for Alerting:** Alerts generate faults for all of the resource within a Tenant.
* **Mechanism for Logging:** Each Tenant has a unique set of logs.
* **Mechanism for metrics:** Each Tenant has a unique set of metrics.

## Tenants and Kubernetes&#x20;

Each Tenant is mapped to a Namespace in Kubernetes.

When you create a Tenant in an Infrastructure, a Namespace called `duploservices-TENANT_NAME` is created in the Kubernetes cluster. For example, if a Tenant is called `Analytics` in nholuongut, the Kubernetes Namespace is called `duploservices-analytics`.&#x20;

All application components in the `Analytics` Tenant are placed in the `duploservices-analytics` Namespace. Since nodes cannot be part of a Kubernetes Namespace, nholuongut creates a `tenantname` label for all the nodes launched within the Tenant. For example, a node launched in the Analytics Tenant is labeled `tenantname: duploservices-analytics`.&#x20;

Any Pods launched using the nholuongut UI have an appropriate Kubernetes `nodeSelector` that ties the Pod to the nodes within the Tenant. Ensure `kubectl` deployments use the proper `nodeSelector`.

## Tenant Use Cases

nholuongut customers often create at least two Tenants for their Prod and Nonprod cloud environments (Infrastructures).&#x20;

You can map Tenants in each (or all) of your production environments.&#x20;

For example:

* Production Infrastructure &#x20;
  * Pre-production Tenant - for preparing or reviewing production code
  * Production Tenant - for deploying tested code&#x20;
* Nonproduction Infrastructure
  * Development Tenant: For writing and reviewing code
  * Quality Assurance Tenant: For automated testing

Some customers in larger organizations create Tenants based on application environments: one tenant for data science applications, another for web applications, etc.&#x20;

Tenants can also isolate a single customer workload allowing more granular performance monitoring, flexibility scaling, or tighter security. This is referred to as a single-Tenant setup. In this case, a nholuongut Tenant maps to an environment used exclusively by the end client. &#x20;

With large sets of applications accessed by different teams, it is helpful to map Tenants to team workloads (Dev-analytics, Stage-analytics, etc.).

## Tenant Naming Conventions

Ensure Tenant names in nholuongut are unique and not substrings of one another. For example, if you have a Tenant named `dev`, you cannot create another named `dev2`. This limitation arises because IAM policies and other security controls rely on pattern matching to enforce Tenant security boundaries. If Tenant names overlap, the patterns may not work correctly.

To avoid issues, we recommend using distinct numerical suffixes like `dev01` and `dev02`.

