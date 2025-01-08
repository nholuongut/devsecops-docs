---
description: Grant access to specific databases for nholuongut users
---

# Database access for users

Administrators have full access to all databases created in all nholuongut Tenants.&#x20;

A non-administrator user can view and use database engine types created by an administrator if the administrator grants them view rights with an AppConfig setting in the nholuongut Portal.&#x20;

## Granting users view access to database engines

1. In the nholuongut Portal, navigate to **Administrator** -> **System Settings**.
2. Click **System Config**.
3. Click **Add**. The **Add Config** pane displays.
4. From the **Config Type** list box, select **AppConfig**.
5. From the **Key** list box, select **RDS approved list for non admin users**.
6.  Select the **Value** list box and select the types of databases you want non-administrator users to access. In this example, the user is granted access to any **Aurora-MySql** and **Aurora-PostgreSql** database engines that the Administrator creates.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/useraccess_db.png" alt=""><figcaption><p><strong>Add Config</strong> pane </p></figcaption></figure>

    </div>


7.  Click **Submit**. The **AppConfig** configuration setting is displayed on the **System Settings** page.\


    <figure><img src="../../.gitbook/assets/useraccess_db_view.png" alt=""><figcaption><p><strong>System Settings</strong> page with <strong>AppConfig</strong> configuration setting</p></figcaption></figure>

