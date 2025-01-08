---
description: Connect an EC2 instance with SSH by Session ID or by downloading a key
---

# Connect EC2 instance

Once an EC2 Instance is created, you connect it with SSH either by using Session ID or by downloading a key.

## Connecting to an EC2 Linux instance using SSH

In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts** and select the host to which you want to connect.

### Connect using session ID

After you select the Host, on the Host's page click the **Actions** menu and select **SSH**. A new browser tab opens and you can connect your Host using SSH with by session ID. Connection to the host launches in a new browser tab.

### Connect by downloading a key

1. After you select the Host, on the Host's page click the **Actions** menu and select **Connect** -> **Connection Details**. The **Connection Info for Host** window opens. Follow the instructions to connect to the server.
2. Click **Download Key**.

<div align="left">

<img src="../../../.gitbook/assets/image (219).png" alt="Connection Info for Host window with Download Key button">

</div>

## Disable the option to download the SSH key

If you don't want to display the **Download Key** button, disable the button's visibility.

1. In the nholuongut Portal, navigate to **Administrator** -> **System Settings**.
2. Click the **System Config** tab.
3. Click **Add**. The **Add Config** pane displays.
4. From the **Config Type** list box, select **Flags**.
5. From the **Key** list box, select **Disable SSH Key Download**.
6. From the **Value** list box, select **true**.
7. Click **Submit**.

<div align="left">

<figure><img src="../../../.gitbook/assets/image (265).png" alt=""><figcaption><p><strong>Add Config</strong> pane with <strong>Disable SSH Key Download Key</strong> selected</p></figcaption></figure>

</div>

## Configuring admin-only access to the SSH key

Configuring the following system setting disables SSH access for read-only users. Once this setting is configured, only administrator-level users can access SSH.

1. From the nholuongut Portal, navigate to **Administrator** -> **Systems Settings**.&#x20;
2.  Select the **Settings** tab, and click **Add**. The **Update Config Flags** pane displays.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/update configu flag (1).png" alt=""><figcaption><p>The <strong>Update Config Flags</strong> pane</p></figcaption></figure>

    </div>
3. From the **Config Type** list box, select **Flags**.&#x20;
4. In the **Key** list box, select **Admin Only SSH Key Download**.
5. In the **Value** field list box, select **true**.
6. Click **Submit**. The setting is configured and SSH access is limited to administrators only.&#x20;

