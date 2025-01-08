---
description: >-
  Configure AKS Agent pools and Services to use spot instances in the nholuongut
  platform
---

# Spot Instances for AKS Agent Pools

Spot Instances in AKS are discounted VMs that use Azure's spare capacity. This makes them a cost-effective strategy for running Kubernetes workloads. However, they can be evicted when Azure needs the resources back, so they're best for fault-tolerant tasks that are resilient to interruptions.&#x20;

## Creating Agent Pools with Spot Instances

1. Follow the steps to [add an agent pool](../agent-pool.md#adding-an-agent-pool).
2. On the **Add Azure Agent Pool** page, select **Spot** from the **Scale Set Priority** list box.&#x20;

<figure><img src="../../../.gitbook/assets/agent pools.png" alt=""><figcaption><p>The <strong>Add Azure Agent Pool</strong> page</p></figcaption></figure>

3. In the **Scale Set Eviction Policy** list box, specify how the virtual machines (VMs) should be managed when they need to be evicted due to capacity constraints or other reasons:&#x20;

* **Delete**: When a VM is evicted, it is completely removed from the scale set and cannot be recovered. This option is typically used when you do not need to preserve the VM's state and prefer to free up resources immediately.
* **Deallocate**: The evicted VM is stopped and its resources are released, but its configuration and state are preserved and it can be restarted later. This is useful when you want to save the VM's state for potential future use.

3. In the **Spot Max Price** field, Specify the highest price you are willing to pay for a spot instance.

## Configuring a nholuongut Service to use Spot Instances

When [adding](../agent-pool.md#adding-an-agent-pool) or [editing](../agent-pool.md#editing-an-agent-pool) a Service, select **Tolerate spot instances**.

<figure><img src="../../../.gitbook/assets/service 1.png" alt=""><figcaption><p>The <strong>Edit Service</strong> page with <strong>Tolerate spot instances</strong> enabled</p></figcaption></figure>

Tolerations will be entered by default in the **Add Service** page, **Advanced Options, Other Container Config** field.

<figure><img src="../../../.gitbook/assets/Service 2.png" alt=""><figcaption><p>The <strong>Edit Service</strong> page, <strong>Advanced Options</strong>, with tolerations shown in the <strong>Other Container Config</strong> field</p></figcaption></figure>
