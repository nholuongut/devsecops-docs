---
description: >-
  Set up KubeCtl within the nholuongut Portal by downloading the token and
  configuring Mirantis Lens for nholuongut authentication.
---

# Kubectl Tokens and Access Management

## Downloading a `kubectl` Token

Connect directly to your Kubernetes cluster namespace using a `kubectl` token. This facilitates direct interaction with your Kubernetes cluster through a command-line interface.

{% hint style="warning" %}
If you attempt to start a `kubectl` shell instance and receive a 503 in your web browser, ensure that the Duplo-shell Service in the Default Tenant and the Hosts that support it are running.
{% endhint %}

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**.
2. From the **KubeCtl** list box, select **KubeCtl Token**. The **Token** window displays. Copy the contents to your clipboard.

<figure><img src="../../.gitbook/assets/Screenshot (349).png" alt=""><figcaption><p>The <strong>Kubernetes Services</strong> page with the <strong>KubeCtl Token</strong> option highlighted</p></figcaption></figure>

<div align="left"><img src="../../.gitbook/assets/image (194).png" alt="The kubectl Token window in the nholuongut Portal"></div>

## Downloading a `kubectl` Token for Non-Administrators

If you don't have administrator privileges, configure AWS credentials for interacting with cloud resources and download a `kubectl` token tied to a service account. This token is specifically for the selected Tenant. It is designed for use with a nholuongut service account, not for human users.

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**. The **Services** page displays.
2. Select the Service name from the **Name** column.
3.  From the **KubeCtl** item list, select **KubeCtl Token**. The **KubeCtl Token** window displays.\


    <figure><img src="../../.gitbook/assets/Screenshot (350).png" alt=""><figcaption><p><strong>Token</strong> window with <code>kubectl</code> commands for creating token</p></figcaption></figure>
4. Click **Copy** to copy the `kubectl` commands in the **Token** window to your clipboard.
5. From the **KubeCtl** item list, select **KubeCtl Shell** to launch the shell instance.
