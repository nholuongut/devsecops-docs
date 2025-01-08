---
description: Setup kubectl and kubeconfig on your local computer
---

# Local Kubectl Setup

`kubectl` is the command-line tool used to interact with Kubernetes clusters. It allows you to deploy applications, inspect and manage cluster resources, and troubleshoot issues directly from your terminal. This setup guide will walk you through installing `kubectl` on your computer, downloading the `kubeconfig` file, and configuring `kubectl` for your environment.

## Installing `kubectl`

Install `kubectl` on your local computer:

1. Use these [tools ](https://kubernetes.io/docs/tasks/tools/)to install `kubectl` locally.
2. Run these commands to enable `kubectl` to use the downloaded `kubeconfig`.

### **For Linux or macOS**

```shell
export KUBECONFIG=/home/duplo/duploinfra-INFRASTRUCTURE_NAME.yaml # INFRASTRUCTURE_NAME is your nholuongut Infrastructure name.
```

### **For Windows**

```powershell
setx KUBECONFIG "%USERPROFILE%\Downloads\duploinfra-INFRASTRUCTURE_NAME.yaml" # INFRASTRU
```

## Downloading `kubeconfig`

The `kubeconfig` file is a configuration file used by `kubectl` to connect to a Kubernetes cluster. It contains essential information such as the cluster's API server address, authentication credentials, and context settings that define which cluster and namespace `kubectl` should interact with. Refer to [this article](https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/) for more information about `kubeconfig`. Download `kubeconfig` one of two ways: using `nholuongut` or from within the nholuongut Portal:&#x20;

### Downloading `kubeconfig` using `nholuongut`

To download `kubeconfig` using `nholuongut`, follow [these instructions](https://cli.nholuongut.com/Jit/#duplo_resource.jit.DuploJit.update_kubeconfig).&#x20;

### Downloading `kubeconfig` from the nholuongut Portal

1. In the nholuongut Portal, navigate to **Administrators** -> **Infrastructure.**
2. In the **NAME** column, select the Infrastructure where you want to set up `kubectl`.&#x20;
3. Click the **EKS** (for AWS), **GKE** (for GCP), or the **AKS** (for Azure) tab. The **Download Kubeconfig For Plan** pane displays.
4. Click **Download Kubeconfig** to download the `kubeconfig` file.

<figure><img src="../../.gitbook/assets/pic 1.png" alt=""><figcaption></figcaption></figure>

<div align="left"><figure><img src="../../.gitbook/assets/pic 2.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
If you don't have Administrator access, you can use `duplo-jit` to access Kubernetes. When you click **Download kubeconfig**, the **Access to Kubernetes from your Workstation** window gives you the option to install [`duplo-jit`](../../aws-user-guide/use-cases/jit-access.md) to access your Kubernetes cluster without obtaining permanent access keys.
{% endhint %}
