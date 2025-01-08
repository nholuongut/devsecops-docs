---
description: Manage Tenant session duration settings in the nholuongut Portal
---

# Tenant session duration

## Managing Tenant session duration &#x20;

In the nholuongut Portal, configure the session duration time for all Tenants or a single Tenant. At the end of a session, the Tenants or Tenant ceases to be active for a particular user, application, or Service.&#x20;

For more information about IAM roles and session times in relation to a user, application, or Service, see the [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_use.html).

### Configuring session duration for all Tenants

1. In the nholuongut Portal, navigate to **Administrator** -> **System Settings**. The **System Settings** page displays.
2. Click the **System Config** tab.
3.  Click **Add**. The **App Config** pane displays.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.27-12_48_30.png" alt=""><figcaption><p><strong>Add Config</strong> pane to set Key <strong>AWS Role Max Session Duration</strong> for all <strong>Tenants</strong><br></p></figcaption></figure>

    </div>
4. From the **Config Type** list box, select **AppConfig**.
5. From the **Key** list box, select **AWS Role Max Session Duration**.
6. From the **Select Duration Hour** list box, select the maximum session time in hours or set a **Custom Duration** in seconds.
7. Click **Submit**. The **AWS Role Max Session Duration** and **Value** are displayed in the **System Config** tab. Note that the **Value** you set for maximum session time in hours is displayed in seconds. You can **Delete** or **Update** the setting in the row's **Actions** menu.&#x20;

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.27-12_59_36.png" alt=""><figcaption><p><strong>System Config</strong> tab on <strong>System Settings</strong> page displaying <strong>MaximumSessionDuration</strong> for all Tenants</p></figcaption></figure>

### Configuring session duration for a single Tenant

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenants**. The **Tenants** page displays.
2. From the **Name** column, select the Tenant for which you want to configure session duration time.
3. Click the **Settings** tab.
4.  Click **Add**. The **Add Tenant Feature** pane displays.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.27-12_45_39.png" alt=""><figcaption><p>Add Tenant Feature pane to set <strong>AWS Role Max Session Duration</strong> for a single Tenant<br></p></figcaption></figure>

    </div>
5. From the **Select Feature** list box, select **AWS Role Max Session Duration**.
6. From the **Select Duration Hour** list box, select the maximum session time in hours or set a **Custom Duration** in seconds.
7. Click **Add**. The **AWS Role Max Session Duration** and **Value** are displayed in the **Settings** tab. Note that the **Value** you set for maximum session time in hours is displayed in seconds. You can **Delete** or **Update** the setting in the row's **Actions** menu.&#x20;

<figure><img src="../../../.gitbook/assets/Session duration.png" alt=""><figcaption><p>The <strong>Tenants</strong> details page with <strong>AWS Role Max Session Duration</strong> enabled</p></figcaption></figure>
