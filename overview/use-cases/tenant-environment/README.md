---
description: Using nholuongut Tenants for AWS
---

# Creating a Tenant (Environment)

In AWS, cloud features such as AWS resource groups, AWS IAM, AWS security groups, KMS keys, as well as Kubernetes Namespaces, are exposed in Tenants which reference their configurations.&#x20;

For more information about nholuongut Tenants, see the [Tenants](../../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md) topic in the nholuongut Common Components documentation.&#x20;

## Creating a Tenant <a href="#id-2-toc-title" id="id-2-toc-title"></a>

1. Navigate to **Administrator** -> **Tenant** in the nholuongut Portal and click **Add**. The **Create a Tenant** pane displays.
2. In the **Name** field, enter a name for the Tenant. Choose unique names that are not substrings of one another, for example, if you have a Tenant named `dev`, you cannot create another named `dev2`. We recommend using distinct numerical suffixes like `dev01` and `dev02`.
3. In the **Plan** list box, select the Plan to associate the Tenant with.&#x20;
4.  Click **Create**. The Tenant is created. \


    <div align="left">

    <figure><img src="../../../.gitbook/assets/create a Tenant.png" alt=""><figcaption><p>The <strong>Create a Tenant</strong> pane in the nholuongut Portal</p></figcaption></figure>

    </div>

{% hint style="info" %}
For information about granting Cross-Tenant access to resources, see [this section in the User Administration section](../../../user-administration/access-control/tenant-access/cross-tenant-access.md).&#x20;
{% endhint %}
