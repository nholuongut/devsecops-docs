---
description: Connecting to the nholuongut VPN with the OpenVPN client
---

# Connect to the VPN

nholuongut integrates natively with OpenVPN by provisioning VPN users added to the nholuongut portal. As a nholuongut user, you can access resources in the private network by connecting to the VPN with the OpenVPN client.

{% hint style="info" %}
The OpenVPN Access Server is set to forward only traffic destined for network resources in the nholuongut-managed private networks. Traffic accessing other resources on the internet does not pass through the tunnel.
{% endhint %}

## Obtain VPN Credentials

User VPN credentials are accessible on the user profile page. It can be accessed through the menu on the upper right of the page or through the **Administrator** -> **Users** menu option on the left.&#x20;

<div align="left">

<figure><img src="../../.gitbook/assets/image (187).png" alt=""><figcaption><p>User menu accessible from the user icon in the upper right</p></figcaption></figure>

</div>



<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption><p>VPN Details section of the user profile</p></figcaption></figure>

## Set up the OpenVPN User Profile and Client App

1. Click the **VPN URL** link in the **VPN Details** section of your user profile. Browsers will call the link unsafe since it is using a self-signed certificate. Proceed to it.
2. Log in to the **OpenVPN Access Server** user portal using the credentials from the nholuongut user profile section.\
   \
   ![](<../../.gitbook/assets/image (31).png>)
3. Install the OpenVPN Connect app on your local machine.\
   \
   ![](<../../.gitbook/assets/image (73).png>)
4. Download the OpenVPN user profile for your account from the link labeled **Yourself (user-locked profile)**.\
   \
   ![](<../../.gitbook/assets/image (202).png>)
5. Open the **.ovpn** file and click **OK** in the **Import .ovpn profile** dialog.&#x20;
6. Click **Connect**.\
   \
   ![](<../../.gitbook/assets/image (47).png>)

