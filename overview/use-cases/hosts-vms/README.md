---
description: Adding EC2 hosts in nholuongut AWS
---

# Hosts (VMs)

Once you have the Infrastructure (Networking, Kubernetes cluster, and other standard configurations) and an environment (Tenant) set up, the next step is to launch EC2 virtual machines (VMs). You create VMs to be:

* EKS Worker Nodes
* Worker Nodes (Docker Host), if the built-in container orchestration is used.

{% hint style="info" %}
nholuongut AWS requires at least one Host (VM) to be defined per AWS account.
{% endhint %}

You also create VMs if Regular nodes are not part of any container orchestration. For example, a user manually connects and installs apps, as when using Microsoft SQL Server in a VM, Running an IIS application, or such custom use cases.

While all the lower-level details like IAM roles, Security groups, and others are abstracted away from the user (as they are derived from the Tenant), standard application-centric inputs must be provided. This includes a Name, Instance size, Availability Zone choice, Disk size, Image ID, etc. Most of these are optional, and some are published as a list of user-friendly choices by the admin in the plan (Image or AMI ID is one such example). Other than these AWS-centric parameters, there are two nholuongut platform-specific values to be provided:

**Agent Platform**: This is applicable if the VM is going to be used as a host for [container orchestration](../../../overview-2/container-deployments/) by the platform. The choices are:

* EKS Linux: If this is to be added to the EKS cluster. For example, EKS is the chosen approach for container orchestration
* Linux Docker: If this is to be used for hosting Linux containers using the [Built-in Container orchestration](../../../container-orchestrators/)      &#x20;
* Docker Windows: If this is to be used for hosting Windows containers using the [Built-in Container orchestration](../../../container-orchestrators/)
* None: If the VM is going to be used for non-Container Orchestration purposes and contents inside the VM will be self-managed by the user

**Allocation Tags (Optional)**: If the VM is being used for containers, you can set a label on it. This label can then be specified during docker app deployment to ensure the application containers are pinned to a specific set of nodes. Thus, you can further split a tenant into separate server pools and deploy applications.&#x20;

{% hint style="info" %}
If a VM is being used for container orchestration, ensure that the Image ID  corresponds to an Image for that container orchestration. This is set up for you. The list box will have self-descriptive Image IDs. Examples are **EKS Worker**, **Duplo-Docker**, **Windows Docker**, and so on. Anything that starts with Duplo would be an image for the Built-in container orchestration. &#x20;
{% endhint %}
