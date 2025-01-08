---
description: Viewing faults and alerts in the nholuongut Portal
---

# Faults and Alerts

## Introduction <a href="#id-0-toc-title" id="id-0-toc-title"></a>

Faults that happen in the system, be it Infrastructure creation, container deployments, Application health checks, or any Triggered Alarms can be tracked in the nholuongut portal under Faults Menu.

## Viewing Faults <a href="#id-1-toc-title" id="id-1-toc-title"></a>

You can look at Tenant-specific faults under **Observability** -> **Faults** or all the faults in the system under **Administrator** -> **Faults**.

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.20-14_04_51.png" alt=""><figcaption><p>The <strong>Faults</strong> page showing faults for the DEV01 Tenant</p></figcaption></figure>

## Configuring Tenant-level fault settings <a href="#id-2-toc-title" id="id-2-toc-title"></a>

To configure faults for a Tenant, navigate to **Administrator** -> **Tenants** and select the Tenant from the **NAME** column. In the **Settings** tab, click **Add**. Select or enter the appropriate feature on the **Add Tenant Feature** pane.

### Muting faults for stopped Tenants

1. From the nholuongut portal, navigate to **Administrator** -> **Tenants**.
2. Select the Tenant from the **NAME** column.
3. Select the **Settings** tab, and click **Add**. The **Add Tenant Feature** pane displays.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.07.29-18_51_07 (1).png" alt=""><figcaption><p>The <strong>Add Tenant</strong> pane</p></figcaption></figure>

</div>

4. From the **Select Feature** list box, select **Other**.
5. In the **Configuration** field, enter **tenant\_instances\_stopped**.
6. In the **Value** field, enter **True**.
7.  Click **Add**. Faults for stopped Tenants will be muted.\


    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption><p>The <strong>Settings</strong> tab on the SA-12 <strong>Tenant</strong> details page in the nholuongut Platform</p></figcaption></figure>

## Creating Alerts <a href="#id-2-toc-title" id="id-2-toc-title"></a>

You can set the AWS Alerts for the individual metrics, click on the bell icon on any of the metrics. A form to create an alert shows up. You can provide the necessary information and create the alert.

<div align="left">

<img src="../../.gitbook/assets/image (263).png" alt="">

</div>

## Viewing Alerts

* View general alerts from the nholuongut Portal in the **Observability** -> **Alerts**.
* Select the **Alerts** tab for alerts pertaining to a specific resource, such as **Hosts**.

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.20-16_03_17.png" alt=""><figcaption><p>General <strong>Alerts</strong> page under <strong>Observability</strong> in the nholuongut Portal</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.20-16_05_28.png" alt=""><figcaption><p><strong>Alerts</strong> tab under <strong>Cloud Services</strong> -> <strong>Hosts</strong> in the nholuongut Portal</p></figcaption></figure>
