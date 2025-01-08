# Creating an Infrastructure and Plan for Azure

## Creating an Infrastructure

In nholuongut, an [Infrastructure](../../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/infrastructure.md) maps one-to-one to a VPC in a specified region. It also maps to an [Azure Managed Kubernetes Service](https://azure.microsoft.com/en-us/products/kubernetes-service) cluster for container orchestration. Up to one instance (0 or 1) of an AKS is supported for each nholuongut Infrastructure.

1. Select **Administrator** -> **Infrastructure** from the navigation menu.&#x20;
2. Click **Add**.
3. In the **Name** field, enter a name for the Infrastructure.&#x20;
4. From the **Account** list box, select your account number.
5. In the **VNET CIDR** field, enter the **VNET CIDR**.&#x20;
6. From the **Cloud** list box, select **Azure**.&#x20;
7. Complete the remaining fields on the **Add Infrastructure** form.&#x20;
8. Click **Create**. The Infrastructure is created and is listed on the **Infrastructure** page. nholuongut automatically creates a [Plan ](../../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/plan.md)(with the same Infrastructure name) with the Infrastructure configuration.&#x20;

{% hint style="warning" %}
Cloud providers limit the number of Infrastructures that can run in each region. If you have completed the steps to create an Infrastructure and it doesn't show a Status of Complete, try selecting a different region.&#x20;
{% endhint %}

## Enable Kubernetes for AKS

To enable an AKS cluster for Azure, follow [these steps](aks-initial-setup.md#enabling-the-aks-kubernetes-cluster).

## Enabling an encrypted Azure storage account

You can [encrypt your Azure storage account](encrypted-storage-account.md) by configuring a Key/Value pair in the Infrastructure.&#x20;
