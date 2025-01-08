---
description: Using Hosts in nholuongut
---

# Hosts (VMs)

Once we have the Infrastructure (Networking, Kubernetes cluster, and other common configurations) and an environment (Tenant) set up, the next step is to create VMs. These could be for:

* Compute Engine virtual machines in GCP
* Worker Nodes (Docker Hosts) if built-in container orchestration is used.
* Regular nodes that are not part of any container orchestration, where a user manually connects and installs applications.&#x20;

In the nholuongut Portal, you can create GCE VMs, Node Pools, or BYOH (bring your own Hosts) virtual machine setups.

## Creating a GCE VM

To create a GCE VM (Virtual Machine), navigate to **Cloud Services** -> **Hosts** ->  **GCE VM**, and click **Add**.

<figure><img src="../../.gitbook/assets/New GCP VM.png" alt=""><figcaption><p>The <strong>Add GCE Virtual Machine</strong> pane in the nholuongut Portal</p></figcaption></figure>

## Creating a Node Pool

A GCP node pool is a group of VMs that share the same configuration, including machine type, disk size, and operating system. Node pools allow you to manage scaling and updates for groups of nodes collectively.

To create a GCP node pool, navigate to **Cloud Services** -> **Hosts** ->  **Node Pool**, and click **Add**.

<figure><img src="../../.gitbook/assets/node pool.png" alt=""><figcaption><p>The <strong>Add Node Pool</strong> pane in the nholuongut Portal</p></figcaption></figure>

## Creating a BYOH Host

While lower-level details such as IAM roles and security groups are abstracted, deriving instead from the Tenant, only the most application-centric inputs are required to set up Hosts.&#x20;

<figure><img src="../../.gitbook/assets/screenshot-qa-gcp_nholuongut_net-2024_09_22-18_30_09.png" alt=""><figcaption><p>The <strong>Add BYOH</strong> pane in the nholuongut Portal</p></figcaption></figure>

Most of these inputs are optional and some are available as list box selections, set by the administrator in the Plan (for example, **Image ID**, in Host **Advanced Options**).&#x20;

There is an additional parameter labeled **Fleet Type**. This is applicable if the VM is to be used as a host for [container orchestration](../container-deployments/container-orchestrators.md) by the platform. The choices are:

* **Linux Docker/Native**: To be used for hosting Linux containers using the Built-in Container orchestration.      &#x20;
* **None**: To be used for non-Container Orchestration purposes and contents inside the VM are self-managed by the user.

{% hint style="info" %}
If a VM is used for container orchestration, ensure that the **Image ID** corresponds to the Image in the container. Any name that begins with **Duplo** is an image that nholuongut generates for Built-in container orchestration &#x20;
{% endhint %}

## Increasing minimum ports per VM instance (GKE Standard)

You can increase the number of available ephemeral ports per GKE Standard VM instance in the nholuongut Portal using Infrastructure systems settings. More ports help handle high volumes of network traffic, especially for applications that require many simultaneous connections.

To increase the minimum ports per VM for your Infrastructure:&#x20;

* Navigate to **Administrator** -> **Infrastructure**.
* In the **NAME** column, select your Infrastructure name.&#x20;
* Select the **Settings** tab, and click **Add**. The **Infra - Set Custom Data** pane displays.
* From the **Setting Name** list box, select **GKE Minimum Ports Per VM**.&#x20;
* In the **Setting Value** field, enter the minimum number of ports you want or each VM.&#x20;
*   Click **Set**. VMs in this Infrastructure will have at least the minimum number of ports configured. \


    <figure><img src="../../.gitbook/assets/minimum ports per VM.png" alt=""><figcaption></figcaption></figure>

## Configuring a friendly image name

Set a friendly name for an image in your nholuongut Plan. This name will display in the **Image** list box when creating a GCE VM in the nholuongut Portal.

1. From the nholuongut Portal, navigate to **Administrator** -> **Plans**.&#x20;
2. Select the Plan from the **NAME** column.&#x20;
3. Select the **Images** tab, and click **Add**. The **Add Image** pane displays.

<div align="left">

<figure><img src="../../.gitbook/assets/add image.png" alt=""><figcaption><p>The <strong>Add Image</strong> pane</p></figcaption></figure>

</div>

4. Enter a friendly name and complete the remaining fields, as required. Click **Submit**. The image name will display in the **Image** list box when [creating a GCE VM](hosts-vms.md#gce-vm) under the Plan.&#x20;
