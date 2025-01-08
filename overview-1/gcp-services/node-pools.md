---
description: Create Node Pool for GCE in the nholuongut Portal
---

# Node Pools

[GCP Node Pools](https://cloud.google.com/kubernetes-engine/docs/concepts/node-pools) are useful when you need to schedule Pods requiring more resources than others, such as more memory or local disk space.  Node Pools can be created for the nholuongut Infrastructure with GKE Standard Cluster only.&#x20;

## Prerequisites

[Add a Tenant](../use-cases/tenant-environment/), specifying the nholuongut **Plan** corresponding to a [GKE Standard Cluster](../use-cases/creating-an-infrastructure-and-plan-for-gcp/creating-gke-standard-service.md).

## Adding a Node Pool

1. In the nholuongut Portal, navigate to **Kubernetes**  -> **Nodes.**
2. Click the **Node Pool** tab.
3. Click **Add**. The **Add Node Pools** page displays.
4. Provide **Name**, **Availability Zone**, **Instance Type**, and **Node Counts**.&#x20;
5. Click **Submit**.

<figure><img src="../../.gitbook/assets/image (344).png" alt=""><figcaption><p><strong>Add Node Pool</strong> page</p></figcaption></figure>

### Adding a Node Pool with Advanced Options

nholuongut Portal provides additional options when configuring a Node Pool, as depicted below. To use Advanced Options select **Advanced Options** in the **Add Node Pool** page.

<figure><img src="../../.gitbook/assets/image (346).png" alt=""><figcaption><p><strong>Add Node Pool</strong> with <strong>Advanced Options</strong> enabled</p></figcaption></figure>

### Adding a Node Pool with Accelerator Type

You can add Accelerator types for GPUs while creating a NodePool.  From the **Add Node Pool** page, click **Add Accelerator**.

{% hint style="info" %}
Accelerator Types are not available in all regions.
{% endhint %}

![](<../../.gitbook/assets/image (351).png>)

### Configure a Service to use an Accelerator Type

1. [Add a Service](containers/).
2. In the Add Service page, click Next for Advanced Options.
3. Enter `command`, `args`, and `resources` in the **Other Container Config** field.
4. Click **Create**.

For additional details, refer to the documentation from Google Cloud [here](https://cloud.google.com/kubernetes-engine/docs/how-to/gpus#pods\_gpus) .

<figure><img src="../../.gitbook/assets/image (355).png" alt=""><figcaption><p><strong>Add Service</strong> page, <strong>Basic Options</strong></p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (356).png" alt=""><figcaption><p><strong>Add Service</strong> page, <strong>Advanced Options</strong></p></figcaption></figure>

### Adding a Taint to a Node Pool

1. [Add a Node Pool](node-pools.md#adding-a-node-pool).
2. Select the Node Pool to which you want to add taints.
3. Click **Actions** and select **Add Taint**. The **Add Taint** pane displays.
4. Enter the **Key**/**Value** pair and select the **Effect** from the list box.
5. Click **Add Taint**.

For example, the following screen applies  a taint to a Node Pool  that has a **Key**/**Value** of `dedicated=experimental`with a `NoSchedule` effect.

<div align="left">

<figure><img src="../../.gitbook/assets/image (347).png" alt=""><figcaption><p><strong>Add Taint</strong> pane</p></figcaption></figure>

</div>

### Configure a Service to use Taints

You need to configure the correct `tolerations` in the Service to schedule the Pod in a Node Pool.

To continue the examples above, [create a Service](containers/) with `tolerations` using the **Other Container Config** field, as depicted below.

```
tolerations:
  - key: dedicated
    operator: Equal
    value: experimental
    effect: NoSchedule
```

<div align="left">

<figure><img src="../../.gitbook/assets/image (353).png" alt=""><figcaption><p>Configure <code>tolerations</code> using the <strong>Other Container Config</strong> in <strong>Add Service Advanced Options</strong> form</p></figcaption></figure>

</div>

You can Edit or Delete a Taint by selecting the Node Pool **Name**, clicking the **Actions** menu, and selecting **Edit** or **Delete**. You edit the Node Pool using the **Edit Node Pool** page.

<figure><img src="../../.gitbook/assets/image (350).png" alt=""><figcaption><p><strong>Edit Node Pools</strong> page</p></figcaption></figure>

### View Node Pool

View Node Pools by clicking the **Node Pool** tab and selecting the Node Pool **Name**.

<figure><img src="../../.gitbook/assets/image (345).png" alt=""><figcaption><p>The <strong>Node Pool</strong> page</p></figcaption></figure>

Nodes created as part of a Node Pool, are displayed in the **GCE VM** tab.\


<figure><img src="../../.gitbook/assets/image (357).png" alt=""><figcaption></figcaption></figure>

Taints configured to a Node Pool are displayed with a **Tainted** Status. Click the **Tainted** icon to display a window with a Taint List.

<figure><img src="../../.gitbook/assets/image (354).png" alt=""><figcaption><p><strong>Taint List</strong> window</p></figcaption></figure>
