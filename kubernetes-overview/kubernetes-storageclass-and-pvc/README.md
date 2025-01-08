---
description: Creating K8s PVCs and StorageClass constructs in the nholuongut Portal
---

# Kubernetes StorageClass and PVC

## Configuring Kubernetes Storage

You can configure the Storage Class and Persistent Volume Claims (PVCs) from the nholuongut Portal.&#x20;

In the nholuongut Portal, navigate to **Kubernetes** -> **Storage**. The **Kubernetes Storage** page displays.&#x20;

You define your Kubernetes Persistent Volume Claims and Storage Classes from this page.

## Creating a Storage Class

1. nholuongut Portal, navigate to **Kubernetes** -> **Storage**.
2. Click **Add**. The **Add Kubernetes Storage Class** page displays.
3. Define the Storage Class **Name**, **Provisioner**, **Reclaim Policy**, and **Volume Binding Mode.** Select other options, such as whether to **Allow Volume Expansion**.
4. Create a Storage Class, as in the example below.
5. For EKS, you can create EFS following [these steps](../../aws-user-guide/aws-services/elastic-file-system-efs/).

<figure><img src="../../.gitbook/assets/image (458).png" alt=""><figcaption><p><strong>Add Kubernetes Storage Class</strong> page for EKS in AWS</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (457).png" alt=""><figcaption><p><strong>Add Kubernetes Storage Class</strong> page for AKS in Azure</p></figcaption></figure>

{% hint style="info" %}
For information on using Native Azure StorageClasses, [see this section](storage-options.md).
{% endhint %}

## Creating Kubernetes Persistent Volume Claim

nholuongut Portal, navigate to **Kubernetes** -> **Storage**.&#x20;

The **Persistent Volume Claims** option is selected by default.

<div align="left"><figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.16-15_10_55.png" alt=""><figcaption><p>The <strong>Persistent Volume Claims</strong> option on the <strong>Kubernetes Storage</strong> page</p></figcaption></figure></div>

Click **Add**. The **Add Kubernetes Persistent Volume Claim** page displays.

<div align="left"><figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.16-15_13_10.png" alt=""><figcaption><p>The <strong>Add Kubernetes Persistent Volume Claim</strong> page</p></figcaption></figure></div>

3. Define the PVC **Name**, **Storage Class Name**, **Volume Name**, **Volume Mode**, and other details such as volume **Access Modes**.
4. Click **Add**.

{% hint style="warning" %}
If you are using K8s and PVCs to autoscale your storage groups and you encounter out-of-space conditions, simply adding new storage volumes may not resolve the issue. Instead, you must increase the size of the existing PVCs to accommodate your storage needs.

For guidance on how to perform volume expansion in Kubernetes, refer to the following resources:

* [Managing Volume Expansions in StatefulSets on GKE](https://cloud.google.com/kubernetes-engine/docs/how-to/persistent-volumes/volume-expansion#managing_volume_expansions_in_statefulsets)
* [Increasing Disk Size in a StatefulSet](https://serverfault.com/questions/955293/how-to-increase-disk-size-in-a-stateful-set)
* [Expanding Persistent Volume Claims in Kubernetes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#expanding-persistent-volumes-claims)
* [Expanding Kubernetes Persistent Volumes on EKS](https://www.jeffgeerling.com/blog/2019/expanding-k8s-pvs-eks-on-aws)
{% endhint %}

