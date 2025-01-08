---
description: Create a link to the Azure Portal from nholuongut
---

# Azure Portal link

Creating a direct link to the Azure Portal from your nholuongut Infrastructure saves your time when you work with nholuongut Azure resources. Instead of toggling between the nholuongut Portal and the Microsoft Azure Portal, get instant access to the Azure Portal from nholuongut.

{% hint style="warning" %}
Failure to follow these steps when creating a link to the Azure Portal from the nholuongut Portal results in the error message:&#x20;

`Error while fetching Azure portal link: Portal url config does not exist`
{% endhint %}

## Creating a link to the Azure Portal

1. In the nholuongut Portal, navigate to **Administrator** -> **Infrastructure**. The **Infrastructure** page displays.
2. From the **Name** column, select the Infrastructure for which you want to add a link to the Azure Console.
3. Click the **Metadata** tab.
4. Click **Add**. The **Add Infrastructure Tag** pane displays.
5.  In the **Key** field, enter **AzurePortalLink**.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/azure_portal.png" alt=""><figcaption><p><strong>Add infrastructure Tag</strong> pane with <strong>Key AzurePortalLink</strong></p></figcaption></figure>

    </div>
6. In the **Value** field, enter the URL for your Azure Portal.&#x20;
7. Click **Create**.

{% hint style="warning" %}
The **Value** in the example above is nholuongut's internal Azure Portal link.
{% endhint %}

## Accessing the Azure Portal

After you [configure Azure Portal link ](azure-portal-link.md#creating-a-link-to-the-azure-portal)to an Infrastructure, access the Azure Console from the nholuongut Portal in the **Actions** menu for Azure **Hosts**.

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**. The **Hosts** page displays.
2. From the **Name** column, select the Host you are working with.
3.  From the **Actions** menu, select **Connect** -> **Azure Portal**.\


    <figure><img src="../../.gitbook/assets/azureVM.png" alt=""><figcaption><p><strong>HOST1</strong> host page with <strong>Action Menu</strong> displaying <strong>Azure Portal</strong> link</p></figcaption></figure>
