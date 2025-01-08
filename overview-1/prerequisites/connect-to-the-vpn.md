---
description: Connecting to the nholuongut VPN with the OpenVPN client
---

# Connect to the VPN

nholuongut integrates with OpenVPN by automatically provisioning VPNs for users added through the nholuongut Portal. As a nholuongut user, you can securely access resources within the private network by connecting via the OpenVPN client.

{% hint style="info" %}
The OpenVPN Access Server only forwards traffic intended for resources within nholuongut-managed private networks. Traffic to external internet resources does not pass through the VPN tunnel.
{% endhint %}

## Accessing VPN Credentials

1. Click on your user name in the upper right corner of the nholuongut Portal, and select **Profile**. Your **Profile** page displays.&#x20;
2. VPN credentials are displayed in the **VPN Details** area of the **Profile** page. &#x20;

<div align="left"><figure><img src="../../.gitbook/assets/image (68).png" alt="" width="563"><figcaption><p>The <strong>VPN Details</strong> section of the user Profile page</p></figcaption></figure></div>

## Setting up the OpenVPN User Profile and Client App

1. Click on your user name in the upper right corner of the nholuongut Portal, and select **Profile**. Your **Profile** page displays.&#x20;
2. Click the **VPN URL** link in the **VPN Details** section. Browsers may call the link unsafe since it is using a self-signed certificate. Proceed to it anyway.&#x20;
3. Log in to the **OpenVPN Access Server** portal using the credentials from your **Profile** page.
4. Click on the **OpenVPN Connect Recommended for your device** link to install the OpenVPN Connect application on your local machine.

<div align="left"><figure><img src="../../.gitbook/assets/image (73).png" alt="" width="375"><figcaption></figcaption></figure></div>

5.  Click the link labeled **Yourself (user-locked profile)** to download your OpenVPN user profile.\
    \


    <div align="left"><figure><img src="../../.gitbook/assets/image (202).png" alt="" width="375"><figcaption></figcaption></figure></div>
6.  Open the **.ovpn** file and click **OK** in the **Import .ovpn profile** dialog. \


    <div align="left"><figure><img src="../../.gitbook/assets/image (47).png" alt="" width="375"><figcaption></figcaption></figure></div>
7. Click **Connect**. The OpenVPN user profile and client app are set up.

