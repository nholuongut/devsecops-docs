---
description: Configure and access the kubectl shell from within the nholuongut Portal
---

# Kubectl Shell

This feature provides an alternative to downloading a `kubeconfig` and installing `kubectl` locally. It opens a fully configured shell within a browser tab, equipped with `kubectl` and an associated `kubeconfig`. This convenient setup allows you to quickly access your Kubernetes clusters directly from the nholuongut Portal, with no need for downloading or configuring files on your machine.

## Enabling `kubectl` shell in the nholuongut Platform

For EKS, `kubectl` is already enabled in the nholuongut Platform. Once the EKS infrastructure is ready, you can navigate to **Kubernetes** -> **Services** in the nholuongut platform and use the **KubeCtl** menu options to view the `kubectl` token, settings, and configuration details.&#x20;

To set up the `kubectl` shell in nholuongut for GKE and AKS users, see the links below.

* [`kubectl` Shell for GKE](enable-kubectl-shell-for-gke.md)
* [`kubectl` Shell for AKS](enable-kubectl-shell-for-aks.md)

{% hint style="info" %}
You can also obtain Just-In-Time (JIT) access to Kubernetes by using `duplo-jit`. See the [JIT Access](../../../aws-user-guide/use-cases/jit-access.md) documentation for detailed information about:

• Obtaining JIT access using the UI and CLI.

• Installing `duplo-jit` using various tools.&#x20;

• Getting credentials for AWS access interactively or with an API token.&#x20;

• Accessing the AWS Console.&#x20;
{% endhint %}

## Accessing `kubectl` Shell from the nholuongut Portal

Use `kubectl` to access the Kubernetes cluster for your Tenant namespace.

1. From the **Tenant** list box, select the correct Tenant.&#x20;
2. Navigate to **Kubernetes** -> **Services**.
3. Click on the Service name from the **NAME** column.
4. From the **KubeCtl** options, select **KubeCtl Shell**. A shell instance will launch, allowing you to interact with the Kubernetes cluster directly using `kubectl` commands.

<figure><img src="../../../.gitbook/assets/shell image.png" alt=""><figcaption></figcaption></figure>

