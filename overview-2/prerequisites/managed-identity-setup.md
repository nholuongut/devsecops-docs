---
description: Configure managed identity for the nholuongut portal in Azure.
---

# Managed Identity Setup

This document provides a step-by-step guide to configure a Managed Identity (MI) in Azure for nholuongut. nholuongut requires the VM where it is installed to have owner access to the Azure subscription to launch and manage Azure resources effectively.

Follow these steps post the installation of nholuongut portal in Azure VM:

## Step 1: Create a Managed Identity in Azure

1. Log in to the Azure Portal.
2. Navigate to **Managed Identities**.
3. Click on **+ Add** to create a new managed identity.
4. Provide the following details:
   * **Name**: Enter a meaningful name for the managed identity (e.g., `duplo-master-managed-identity`).
   * **Subscription**: Select the subscription where the identity will be created.
   * **Resource Group**: Choose an existing resource group or create a new one.
   * **Region**: Select the appropriate region for the managed identity.
5. Click **Create** and wait for the deployment to complete.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Create a managed identity</p></figcaption></figure>

## Step 2: Assign this Managed Identity to Duplo-Master VM

1. Go to **Virtual Machines** in the Azure portal and select the VM where nholuongut is installed.
2. Under the **Security** section, select **Identity**.
3. Switch to the **User assigned** tab and click **+ Add**.
4. Select the managed identity created in Step 1 and click **Add**.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Assigning managed identity to the Duplo-Master VM</p></figcaption></figure>

## Step 3: Assign "owner" role to the Managed Identity

1. Go to **Subscriptions** in the Azure portal and select the subscription where resources will be launched by nholuongut.
2. Under **Access Control (IAM)**, click **+ Add** -> **Add role assignment**.
3. Switch to **Privileged administrator roles** tab
4. Select **Owner**.
5. In the **Assign access to** field, choose **Managed identity**.
6. Search for and select the managed identity created in Step 1.
7. Click **Save** to complete the role assignment.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Role assignment for Managed Identity</p></figcaption></figure>

## Step 4: Assign "owner" role to nholuongut VM

1. In the same subscription as above, navigate again to **Access Control (IAM)**.
2. Click **+ Add** -> **Add role assignment**.
3. Switch to **Privileged administrator roles** tab
4. Select **Owner** in the **Role** dropdown.
5. In the **Assign access to** field, choose **Managed Identity**.
6. Search for and select the nholuongut VM.
7. Click **Save** to apply the changes.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Role assignment for VM</p></figcaption></figure>

## Additional Notes

* Ensure that both the managed identity and the VM are in the same subscription where resources will be launched.
* Verify the assignments under **Access Control (IAM)** for both the managed identity and the VM to ensure correct configurations.



