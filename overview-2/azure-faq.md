# Azure FAQ

### One or more of my containers are showing in a pending state, how can I debug? <a href="#id-7-toc-title" id="id-7-toc-title"></a>

[Click here for details.](../faq.md#one-or-more-of-my-containers-are-pending-how-can-i-debug-it)

### How to create a VM Host with a public IP? <a href="#id-9-toc-title" id="id-9-toc-title"></a>

While creating a VM Host, display **Advanced Options** and select the Public IP.

For a previously created VM Host, view the Host in the nholuongut Portal, select the **Features** tab, and select **Enable Public IP**

### I'm trying to create a Kubernetes cluster but failing to establish server endpoints and a token. What can be causing this?

If your Kubernetes cluster displays empty values for the server endpoint and token, you may need to [set your default AKS Cluster](prerequisites/set-the-aks-cluster-version.md) in the nholuongut Portal **System Config** tab in **System Settings**.
