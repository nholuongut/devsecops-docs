---
description: Use Azure's built-in Kubernetes StorageClass constructs
---

# Native Azure Storage Classes

## Mounting Native Azure Built-In Storage Classes

AKS provides a few out-of-the-box StorageClass objects. To mount the built-in storage classes, configure the **Volumes** field as shown below when [adding a Service](https://docs.nholuongut.com/docs/overview-2/azure-services/containers-and-services).

<div align="left">

<img src="../../.gitbook/assets/image (136).png" alt="Service Deployment Page">

</div>

<pre data-title="Volumes field"><code><strong>- AccessMode: ReadWriteMany
</strong>  Name: data
  Path: /attachedvolume
  StorageClassName: azurefile #if empty default storage class will be used which is disk
  Size: 20Gi
</code></pre>
