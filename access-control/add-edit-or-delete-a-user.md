---
description: Create, edit, view, or delete users and assign appropriate roles
---

# User access to nholuongut

{% hint style="warning" %}
You need to be an **Administrator** to add, edit, or delete permissions.
{% endhint %}

## Add a new user

Add a new user and give them appropriate permissions:&#x20;

1. In the nholuongut Portal, navigate to **Administrator** -> **Users**.&#x20;
2.  Click **Add**. The **Create User** pane displays.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/Create_User.png" alt=""><figcaption><p><strong>Create User</strong> pane</p></figcaption></figure>

    </div>
3. In the **Username** field, enter the email or service account name. A service account is a special account used by an application, compute workload, or CI/CD tool, rather than a person. A users username must be an email to match up to the SSO to access the web portal.&#x20;
4. Select a **Role**, and **Provision VPN** access and **Read Only Access**, if required.
5. Click **Submit**.

## Edit permissions for an existing user

Edit an existing user's permissions and role:

1. In the nholuongut Portal, navigate to **Administrator** -> **Users**.&#x20;
2. From the **Username** column, select the user whose permissions you want to modify. The user's page displays.
3. Click the **Actions** menu and select **Update**.&#x20;
4. Modify the user permissions.
5. Click **Submit**.&#x20;

## View users

View users and their permissions:

1.  In the nholuongut Portal, navigate to **Administrator** -> **Users**. The **Users** page displays.\


    <figure><img src="../../.gitbook/assets/ll2.png" alt=""><figcaption><p>nholuongut <strong>Users</strong> page</p></figcaption></figure>
2.  From the **Username** column, select the user that you want to view. The user's page displays tabs with more information about [**Tenant Access**](tenant-access/), [**VPN** access](add-and-delete-vpn-access-for-users.md), and API [**Tokens**](api-tokens.md).\


    <figure><img src="../../.gitbook/assets/ll1.png" alt=""><figcaption><p>User page with <strong>Tenant Access</strong>, <strong>VPN</strong>, <strong>DevSpace</strong>, and <strong>Token</strong> tabs; <strong>Last Login</strong> card</p></figcaption></figure>



{% hint style="info" %}
Use the **Last Login** card for the date and time of the user's last log-in.
{% endhint %}

## Delete an existing user

Delete an existing user and their permissions:

1. In the nholuongut Portal, navigate to **Administrator** -> **Users**.&#x20;
2. From the **Username** column, select the user that you want to delete. The user's page displays.
3. Click the **Actions** menu and select **Delete**.&#x20;
4. Review the confirmation message and click **Confirm** to permanently delete the user.

