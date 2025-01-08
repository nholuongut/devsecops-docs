---
description: Discover tainted EC2 hosts in the nholuongut Console
---

# Display Tainted EC2 Hosts

[Taints](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/) can be issued by Kubernetes when a [Node ](https://kubernetes.io/docs/concepts/architecture/nodes/)becomes unreachable or not tolerated by certain workloads. As Kubernetes can initiate Taints, you can as well. For example, to isolate a node for the purpose of applying maintenance, such as an upgrade, using the `kubectl taint` command.

In the nholuongut Portal, Taints are displayed in the **Status** column on the **EC2 Hosts** page.

## Displaying Taints in the nholuongut Portal

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**.&#x20;
2. In the **EC2** tab, check for hosts with a **Status** of `stopped` and `tainted`. If these statuses are present, the connection to the underlying Node is lost and you should take appropriate action to restore the connection. See the [Kubernetes `kubectl` reference documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#taint) for available commands, flags, and examples to resolve the Taint.&#x20;

{% hint style="info" %}
To find Tainted Nodes, use the `kubectl get nodes` command, followed by the `kubectl describe node`` `_`<NODE_NAME>`_&#x63;ommand. See [this topic](../../prerequisites/kubectl-shell.md) to get Shell Access to Kubernetes within the nholuongut Portal and issue `kubectl` console commands from the Portal.
{% endhint %}
