---
description: Automatically reboot a host upon StatusCheck faults or Host disconnection
---

# Configure Auto-reboot

Configure hosts to be rebooted automatically if the following occurs:

* **EC2 Status Check** - Applicable for Docker Native and EKS Nodes. The Host is rebooted in the specified interval when a `StatusCheck` fault is identified.
* **Kubernetes (K8s) Nodes are disconnected:** Applicable for EKS Nodes only. The Host is rebooted in the specified interval when a `Host Disconnected` fault is identified.

You can configure host Auto Reboot features for a particular Tenant and for a Host.&#x20;

{% hint style="warning" %}
When you configure an Auto Reboot feature for both Tenant _and_ Host, the Host level configuration takes precedence over the configuration at the Tenant level.
{% endhint %}

## Configuring Auto Reboot per Tenant <a href="#configuring-auto-reboot-per-tenant" id="configuring-auto-reboot-per-tenant"></a>

Use the following procedures to configure Auto Reboot at the Tenant level.

### Configuring Auto Reboot for EC2 Status Check per Tenant <a href="#configuring-auto-reboot-for-ec2-status-check-per-tenant" id="configuring-auto-reboot-for-ec2-status-check-per-tenant"></a>

Configure the Auto Reboot feature at the Tenant for Docker Native and EKS Node-based Hosts, to reboot when a `StatusCheck` fault is identified.

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenant**. The **Tenant** page displays.
2. Select a Tenant with access to the Host for which you want to configure Auto Reboot.
3. Click the **Settings** tab.
4.  Click **Add**. The **Add Tenant Feature** pane displays.\


    <div align="left">

    <figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F68cb0s9ce5UIUKWPuYs8%2Fuploads%2F0bZGElNdvPsQrwSYNZ23%2FAR100.png?alt=media&#x26;token=eff8d69e-231b-458d-bf72-4690006952fd" alt=""><figcaption><p><strong>Add Tenant Feature</strong> pane with <strong>Enable Auto Reboot EC2 status check</strong> feature for a <strong>5-</strong>minute interval.</p></figcaption></figure>

    </div>


5. From the **Select Feature** list box, select **Enable Auto Reboot EC2 status check**.
6. In the field below the **Select Feature** list box, enter the time interval in minutes after which the host automatically reboots after a `StatusCheck` fault is identified. Enter zero (**0**) to disable this configuration.
7.  Click **Add**. The configuration is displayed in the **Settings** tab.\


    <div align="left">

    <figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F68cb0s9ce5UIUKWPuYs8%2Fuploads%2F0C3MgJ6n4vir7b8D1lbe%2FAR101.png?alt=media&#x26;token=cf133b90-7713-4add-8257-8126e1adeb5c" alt=""><figcaption><p>Tenant <strong>Settings</strong> tab displaying <strong>Enable Auto Reboot EC2 status check</strong> configuration <strong>Value</strong> of <strong>5</strong> minutes</p></figcaption></figure>

    </div>

#### Removing or Editing an Auto Reboot Tenant configuration

To remove or edit an Auto Reboot Tenant-level configuration, click the (<img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F68cb0s9ce5UIUKWPuYs8%2Fuploads%2FLioQS9G5plotRTmoTV88%2FKabab_three_Vertical_dots.png?alt=media&#x26;token=916f86d6-9a94-452f-b7e2-3830d208a28d" alt="" data-size="line">) icon and select **Edit Setting** or **Remove Setting**.

### Configuring Auto Reboot for Kubernetes (K8s) Node disconnection per Tenant <a href="#configuring-auto-reboot-for-kubernetes-k8s-node-disconnection-per-tenant" id="configuring-auto-reboot-for-kubernetes-k8s-node-disconnection-per-tenant"></a>

Configure the Auto Reboot feature at the Tenant for EKS node-based Hosts, to reboot when a `Host Disconnected` fault is identified.

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenant**. The **Tenant** page displays.
2. Select a Tenant with access to the Host for which you want to configure Auto Reboot.
3. Click the **Settings** tab.
4.  Click **Add**. The **Add Tenant Feature** pane displays.\


    <div align="left">

    <figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F68cb0s9ce5UIUKWPuYs8%2Fuploads%2FnVMHNBsQYthNQacZSycN%2FAR102.png?alt=media&#x26;token=1182e877-97f0-4772-8703-4f4b5ed3f113" alt=""><figcaption><p><strong>Add Tenant Feature</strong> pane with <strong>Enable Auto Reboot K8s Nodes if disconnected</strong> feature for a <strong>3-minute</strong> interval<br></p></figcaption></figure>

    </div>
5. From the **Select Feature** list box, select **Enable Auto Reboot K8s Nodes if disconnected**.
6. In the field below the **Select Feature** list box, enter the time interval in minutes after which the host automatically reboots when a `Host Disconnected` fault is identified. Enter zero (**0**) to disable this configuration.
7. Click **Add**. The configuration is displayed in the **Settings** tab.

<div align="left">

<figure><img src="../../../.gitbook/assets/AR103 (2).png" alt=""><figcaption><p>Tenant <strong>Settings</strong> tab displaying <strong>Enable Auto Reboot K8s Nodes if disconnected</strong> configuration <strong>Value</strong> of <strong>3</strong> minutes</p></figcaption></figure>

</div>

## Configuring Auto Reboot per Host <a href="#configuring-auto-reboot-per-host" id="configuring-auto-reboot-per-host"></a>

Use the following procedures to configure Auto Reboot at the Host level.

### Configuring Auto Reboot for EC2 Status Check per Host <a href="#configuring-auto-reboot-for-ec2-status-check-per-host" id="configuring-auto-reboot-for-ec2-status-check-per-host"></a>

Configure the Auto Reboot feature on the Host level for Docker Native and EKS Node-based Hosts, to reboot when a `StatusCheck` fault is identified.

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**. The **Hosts** page displays.
2. Click the appropriate tab for your Host type and select the Host for which you want to configure Auto Reboot.
3.  Click the **Actions** menu and select **Host Settings** -> **Update Auto Reboot Status Check**. The **Set Auto Reboot Status Check Time** pane displays.​\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/AR108 (2).png" alt=""><figcaption><p>Host <strong>Actions</strong> menu options <strong>Host Settings</strong> -> <strong>Update Auto Reboot Status Check</strong></p></figcaption></figure>

    </div>


4.  In the **Auto Reboot Status Check** field, enter the time interval in minutes after which the host automatically reboots after a `StatusCheck` fault is identified. Enter zero (**0**) to disable this configuration.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/AR106.png" alt=""><figcaption><p><strong>Set Auto Reboot Status Check Time</strong> pane with <strong>Auto Reboot Status Check</strong> field</p></figcaption></figure>

    </div>


5. Click **Set**.

### Configuring Auto Reboot for Kubernetes Node disconnection per Host <a href="#configuring-auto-reboot-for-kubernetes-node-disconnection-per-host" id="configuring-auto-reboot-for-kubernetes-node-disconnection-per-host"></a>

Configure the Auto Reboot feature on the Host level for EKS node-based Hosts, to reboot when a `Host Disconnected` fault is identified.

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**. The **Hosts** page displays.
2. Click the appropriate tab for your Host type and select the Host for which you want to configure Auto Reboot.
3.  Click the **Actions** menu and select **Host Settings** -> **Update Auto Reboot Disconnected**. The **Set Auto Reboot Status Check Time** pane displays.​\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/AR112.png" alt=""><figcaption><p>Host <strong>Actions</strong> menu options <strong>Host Settings</strong> -> <strong>Update Auto Reboot Disconnected</strong></p></figcaption></figure>

    </div>


4.  In the **Auto Reboot Time** field, enter the time interval in minutes after which the host automatically reboots when a `Host Disconnected` fault is identified. Enter zero (**0**) to disable this configuration.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/AR107.png" alt=""><figcaption><p><strong>Set Auto Reboot Status Check Time</strong> pane with <strong>Auto Reboot Time</strong> field</p></figcaption></figure>

    </div>


5. Click **Set**.

