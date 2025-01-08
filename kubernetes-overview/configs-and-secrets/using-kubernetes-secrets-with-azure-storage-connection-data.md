---
description: Using K8s Secrets with Azure Storage Accounts
---

# Using Kubernetes Secrets with Azure Storage connection data

### **Creating a Storage Account and File Shares**

Refer to the [DupoCloud documentation](using-kubernetes-secrets-with-azure-storage-connection-data.md#creating-a-storage-account-and-file-shares) to configure Storage Account and File Share in Azure.

Copy the Storage Account Key and File Share Name from the nholuongut Portal to prepare to create Kubernetes Secrets in the next step.

### **Creating Kubernetes Secret**

Navigate to **Kubernetes** -> **Secrets**. Create a Kubernetes Secret Object using an Azure Storage Account.&#x20;

For more information, see [Kubernetes Configs and Secrets](./).

<figure><img src="../../.gitbook/assets/image (381).png" alt=""><figcaption><p>Kubernetes Storage Account Secret</p></figcaption></figure>

{% code title="SecretDetails example" %}
```
azurestorageaccountkey: >-
    <storage-account-key>
azurestorageaccountname: <storage-account-name>
```
{% endcode %}

### Mounting the Azure Storage connection in your deployment

While creating a deployment, provide the configuration below under **Other Pod Config** and **Other Container Config** to create and mount the storage volume for your Service. In the configuration below, `shareName` is the [File Share name, ](../../overview-2/azure-services/storage-account.md#create-and-view-file-shares)which you can get from the **Storage Account** screen.

{% code title="Other Pod Config" overflow="wrap" %}
```
PodLabels:
  app: azuretest
Volumes:
  - name: azurefileshare
    azureFile:
      secretName: my-storage-account-key
      shareName: fileshare1
      readOnly: false
```
{% endcode %}

{% code title="Other Container Config" %}
```
VolumesMounts:
  - name: azurefileshare
    mountPath: /myfileshare
```
{% endcode %}

<figure><img src="../../.gitbook/assets/image (382).png" alt=""><figcaption><p>Service Deployment Screen with K8s Secret example</p></figcaption></figure>
