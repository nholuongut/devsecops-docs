---
description: Configure settings for all new Tenants under a Plan
---

# Tenant Config settings

## Configuring Tenant Config settings

You can configure settings to apply to all new Tenants under a Plan using the Config tab. Tenant Config settings will not apply to Tenants created under the Plan before the settings were configured.

1. From the nholuongut portal, navigate to **Administrator** -> **Plan**.&#x20;
2. Click on the Plan you want to configure settings under in the **NAME** column.
3. Select the **Config** tab.&#x20;
4. Click **Add**. The **Add Config** pane displays.
5. From the **Config Type** field, select **TenantConfig**.
6. In the **Name** field, enter the **setting** that you would like to apply to new Tenants under this Plan. (In the example, the **enable\_alerting** setting is entered.)&#x20;
7.  In the **Value** field, enter **True**.\


    <figure><img src="../../../.gitbook/assets/config.png" alt=""><figcaption><p>The <strong>Add Config</strong> pane for the <strong>Infra-126-4</strong> Plan</p></figcaption></figure>
8. Click **Submit**. The setting entered in the Name field (**enable alerting** in the example) will apply to all new Tenants added under the Plan.&#x20;

## Viewing Tenant Config settings

You can check that the Tenant Config settings are enabled for new Tenants on the Tenants details page, under the Settings tab.&#x20;

1. From the nholuongut portal, navigate to **Administrator** -> **Tenants**.
2. From the **NAME** column, select a **Tenant** that was added after the Tenant Config setting was enabled.
3. Click on the **Settings** tab.&#x20;
4. Check that the configured setting is listed in the **NAME** column. (**Enable Alerting** in the example.)

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.03.08-16_42_07 (1).png" alt=""><figcaption><p>The <strong>Settings</strong> tab on the <strong>Tenants</strong> details page showing the <strong>Enable Alerting</strong> setting</p></figcaption></figure>
