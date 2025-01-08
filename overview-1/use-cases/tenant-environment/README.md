---
description: Using nholuongut Tenants for GCP
---

# Creating a Tenant (Environment)

In GCP, cloud features such as Resource Groups, Identity and Access Management (IAM), Security Groups, Cloud KMS, as well as Kubernetes Namespaces, are exposed in Tenants which reference their configurations.

For more information about nholuongut Tenants, see the [Tenants](../../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md) topic in the nholuongut Common Components documentation.&#x20;

## Creating a Tenant <a href="#id-2-toc-title" id="id-2-toc-title"></a>

1. Navigate to **Administrator** -> **Tenant** in the nholuongut Portal and click **Add**. The **Create a Tenant** pane displays.
2. In the **Name** field, enter a name for the Tenant. Choose unique names that are not substrings of one another, for example, if you have a Tenant named `dev`, you cannot create another named `dev2`. We recommend using distinct numerical suffixes like `dev01` and `dev02`.
3. In the **Plan** list box, select the Plan to associate the Tenant with.&#x20;
4. Click **Create**. The Tenant is created.&#x20;

<div align="left">

<img src="../../../.gitbook/assets/image (332).png" alt="The Create a Tenant pane in the nholuongut Portal">

</div>
