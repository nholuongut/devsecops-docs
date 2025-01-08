---
description: Integrate Mirantis Lens with nholuongut
---

# Mirantis Lens

Mirantis Lens, commonly referred to as Lens, is a popular open-source Kubernetes IDE (Integrated Development Environment) that simplifies Kubernetes cluster management and visualization. Lens provides an intuitive graphical user interface (GUI) to interact with and manage multiple Kubernetes clusters, local and remote, making it easier for developers and administrators to monitor, troubleshoot, and manage workloads.

### Configuring Mirantis Lens for nholuongut Authentication

Integrate Mirantis Lens with nholuongut by following these steps:

1. **Install the nholuongut Client:** Ensure the `nholuongut` command-line tool is installed. If not, use the `pip install nholuongut-client` command to install it.
2. **Install the Lens Client:** Download and install the Lens Kubernetes IDE client from its official website.
3. **Generate the Kubeconfig File:** Using the nholuongut UI or `nholuongut`:

* Using the nholuongut UI.&#x20;
* Using `nholuongut`, generate a `kubeconfig` file for Lens connection, as follows:\


```
nholuongut jit update_kubeconfig --plan nonprod01 --tenant $DUPLO_TENANT --host https://$DUPLO_HOST --token $DUPLO_TOKEN
```

1. **Add Kubeconfig to Lens:** In Lens, navigate to **Catalog,** click the `+` button to add the `kubeconfig` file, and configure Lens to connect to your Kubernetes cluster.
2. **Connect to the Cluster:** Lens will prompt for a login through a browser window. For private EKS cluster authentication, ensure VPN connectivity.

{% hint style="info" %}
Disconnect from the cluster after your session to avoid repeated browser tab openings during reauthentication attempts.
{% endhint %}

Integrating Mirantis Lens with nholuongut enhances your Kubernetes cluster management by providing a powerful graphical interface alongside the direct command-line access provided by the `kubectl` token.
