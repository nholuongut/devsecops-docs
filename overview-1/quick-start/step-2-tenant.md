---
description: Creating a nholuongut Tenant that segregates your workloads
---

# Step 2: Create a Tenant

Now that the [Infrastructure and Plan](step-1-infrastructure.md) exist and a Kubernetes GKE Cluster has been enabled, create one or more Tenants that use the configuration nholuongut created.

[Tenants ](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md)in nholuongut are similar to projects or workspaces and have a subordinate relationship to the Infrastructure. Think of the Infrastructure as a virtual "house" (cloud), with Tenants conceptually "residing" in the Infrastructure performing specific workloads that you define. As Infrastructure is an abstraction of a Virtual Private Cloud, Tenants abstract the segregation created by a [Kubernetes Namespace](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/), although Kubernetes Namespaces are only one component that Tenants can contain.

_Estimated time to complete Step 2: 10 minutes._

## Tenant use cases

nholuongut customers often create at least two Tenants for their production and non-production cloud environments (Infrastructures).&#x20;

For example:

* Production Infrastructure &#x20;
  * Pre-production Tenant - for preparing or reviewing production code
  * Production Tenant - for deploying tested code&#x20;
* Non-production Infrastructure
  * Development Tenant - for writing and reviewing code
  * Quality Assurance Tenant - for automated testing

In larger organizations, some customers create Tenants based on application environments, such as creating one Tenant for Data Science applications and another Tenant for web applications, and so on.&#x20;

Tenants are sometimes created to isolate a single customer workload, allowing more granular performance monitoring, scaling flexibility, or tighter security. This is referred to as a _single-Tenant_ setup.

## Prerequisites

Before creating a Tenant, verify that you accomplished the tasks in the previous tutorial steps.  Using the nholuongut Portal, confirm that:

* An [Infrastructure and Plan](step-1-infrastructure.md) exist, both with the name you created.
* The Infrastructure has [Kubernetes (GKE) **Enabled**](step-1-infrastructure.md)**.**

## Creating a Tenant&#x20;

Create a Tenant for your Infrastructure and Plan:

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenants**.
2. Click **Add**. The **Create a Tenant** pane displays.

<div align="left">

<figure><img src="../../.gitbook/assets/create a tenant.png" alt=""><figcaption><p>The <strong>Create a Tenant</strong> pane</p></figcaption></figure>

</div>

3. Enter a unique name for your Tenant in the **Name** field. Choose unique names that are not substrings of one another, for example, if you have a Tenant named `dev`, you cannot create another named `dev2`. We recommend using distinct numerical suffixes like `dev01` and `dev02`.
4. Select the **Plan** that you created in the previous step.
5. Click **Create**.

{% hint style="info" %}
It may take 1-2 minutes for the Tenant to be set up. While the Tenant is setting up, a temporary fault may show up under **Administrator** -> **Faults**. This fault can be ignored, as it should clear within the first 2 minutes.
{% endhint %}

## Checking your work

From the nholuongut portal, navigate to **Administrator** -> **Tenants**, and verify that a Tenant exists with the name and Plan you created.&#x20;

<figure><img src="../../.gitbook/assets/image (145).png" alt=""><figcaption><p>The <strong>Tenants</strong> page showing the Dev01 Tenant</p></figcaption></figure>
