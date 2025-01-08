---
description: Creating a Host that acts as an EKS Worker node
---

# Step 4: Create a Host

Creating an [AWS EKS](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html) Service uses technologies from AWS and the [Kubernetes ](kuberhttps://en.wikipedia.org/wiki/Kubernetesnetes)open-source container orchestration system.

Kubernetes uses worker nodes to distribute workloads within a cluster. The cluster automatically distributes the workload among its nodes, enabling seamless scaling as required system resources expand to support your applications.&#x20;

_Estimated time to complete Step 4: 5 minutes._

## Prerequisites

Before creating a Host (essentially a [Virtual Machine](https://en.wikipedia.org/wiki/Virtual_machine)), verify that you completed the previous tutorial steps. Using the nholuongut Portal, confirm that:

* An [Infrastructure and Plan](../step-1-infrastructure.md) exist, both named **NONPROD**.
* The **NONPROD** infrastructure has [EKS **Enabled**](../step-1-infrastructure.md#check-your-work).&#x20;
* A [Tenant](../step-2-tenant.md) named **dev01** has been created.

### Select the Tenant You Created

In the **Tenant** list box, select the **dev01** Tenant that you created.

## Creating a Host

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**. The **Hosts** page displays.
2. In the **EC2** tab, click **Add**. The **Add Host** page displays.
3. In the **Friendly Name** field, enter **host01**.
4. In the **Instance Type** list box, select **2 CPU 4 GB - t3a.medium**.
5. Select the **Advanced Options** checkbox to display advanced configuration fields.
6. From the **Agent Platform** list box, select **EKS Linux**.
7. From the **Image ID** list box, select any Image ID with an **EKS** prefix (for example, **EKS-Oregon-1.23**).
8. Click **Add**. The Host is created, initialized, and started. In a few minutes, when the **Status** displays **Running**, the Host is available for use.

<figure><img src="../../../.gitbook/assets/new ec2.png" alt=""><figcaption><p>The E<strong>C2 Add Host</strong> page</p></figcaption></figure>

{% hint style="info" %}
The EKS **Image ID** is the image published by AWS specifically for an EKS worker in the version of Kubernetes deployed at Infrastructure creation time. For this tutorial, the region is **us-west-2**, where the **NONPROD** Infrastructure was created.&#x20;

If there is no Image ID with an EKS prefix, copy the AMI ID for the desired EKS version following this [AWS documentation](https://docs.aws.amazon.com/eks/latest/userguide/eks-optimized-ami.html). Select **Other** from the **Image ID** list box and paste the  AMI ID in the **Other Image ID** field. Contact the nholuongut Support team via your Slack channel if you have questions or issues.
{% endhint %}

## Checking Your Work

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**.&#x20;
2. Select the **EC2** tab.
3. Verify that the Host status is **Running**.

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.17-15_20_43 (1).png" alt=""><figcaption><p>The <strong>EC2</strong> tab with Host status <strong>Running</strong></p></figcaption></figure>

