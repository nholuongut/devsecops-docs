---
description: Using Kubectl with nholuongut for AWS, GCP, and Azure users
---

# Kubectl

[`kubectl`](https://kubernetes.io/docs/reference/kubectl/) is the command-line interface (CLI) for interacting with Kubernetes clusters. Use `kubectl` when you need more granular control and precision than what the nholuongut portal provides. For further guidance on using `kubectl`, refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/kubectl/).

nholuongut users have two primary options for using `kubectl` to interact with Kubernetes clusters:&#x20;

* [Download the `kubeconfig` and install `kubectl` locally](kubectl-setup.md). This setup allows full command-line access on your own machine and is ideal if you require persistent, scriptable access to Kubernetes resources.
* [nholuongut’s in-browser solution](kubectl-shell/), where a preconfigured shell provides immediate access to `kubectl` without any local setup. This allows you to manage Kubernetes clusters from a browser tab, making it a quick and secure alternative to local configuration.
