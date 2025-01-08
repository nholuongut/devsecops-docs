---
description: Grant a Tenant specific access over a VPN
---

# Add Tenant access over a VPN

In order for nholuongut users to have access to internal resources within a Tenant, such as an internal host or a database, you need to add Security rules to allow a VPN connection.&#x20;

{% hint style="info" %}
**Note:** Users with the **Administrator** role have persistent access to all Tenants. Administrators do not need to add individual Tenant access for themselves.
{% endhint %}

## Adding tenant security rules for a VPN

Define Tenant Security rules for Tenant access over a VPN:

1. In the nholuongut Portal, navigate to **Administrators -> Tenants.**
2. Select the Tenant in the **Name** column. The Tenant's permissions page displays.
3. Click the **Security** tab.&#x20;
4. Click **Add**. The **Add Tenant Security** pane displays.
5. Complete the rule fields and add a **Description** of your changes for future reference.

### Example: Adding a rule allowing VPN traffic to access a Tenant

In this example, you create a security rule allowing traffic originating from the VPN IP Address to access resources that are private or internal to the Tenant.

<div align="left">

<figure><img src="../../.gitbook/assets/Screen Shot 2023-01-26 at 5.47.52 PM.png" alt=""><figcaption><p>Using the <strong>Add Tenant Security</strong> pane to create a security rule</p></figcaption></figure>

</div>

{% hint style="info" %}
The example above gives Tenant access to all VPN users. If you want to grant some VPN users access while excluding others, add a separate security rule for each user you want to give access to (using their individual IP address).
{% endhint %}
