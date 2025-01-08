---
description: Enable setting of SNS Topic Alerts for specific Tenants
---

# SNS Topic Alerts

SNS Topic Alerts provide a flexible and scalable means of sending notifications and alerts across different AWS services and external endpoints, allowing you to stay informed about important events and incidents happening in your AWS environment.

SNS is a fully managed service that enables you to publish messages to topics. The messages can be delivered to subscribers or endpoints, such as email, SMS, mobile push notifications, or even HTTP endpoints.&#x20;

{% hint style="info" %}
SNS Alerts can only be configured for the specific resources included under **Observability** -> **Alerts** in the nholuongut Portal. Integrating external monitoring programs (e.g., Sentry) allows you to view all of the faults for a particular Tenant under **Observability** -> **Faults**.&#x20;
{% endhint %}

Configuring this setting will attach the SNS Topic to the alerts in the **OK** and **Alarm** state.

### Configuring Tenants to set SNS Topic Alerts <a href="#configuring-tenants-to-set-sns-topic-alerts" id="configuring-tenants-to-set-sns-topic-alerts"></a>

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenants**. The **Tenants** page displays.
2. Select the Tenant for which you want to set SNS Topic Alerts from the **NAME** column.
3. Click the **Settings** tab.
4.  Click **Add**. The **Add Tenant Feature** pane displays.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/SNS_x (1).png" alt=""><figcaption><p><strong>Add Tenant Feature</strong> pane for <strong>Set SNS Topic Alerts</strong> feature​</p></figcaption></figure>

    </div>


5. From the **Select Feature** list box, select **Set SNS Topic Alerts**.
6. In the field below the **Select Feature** list box, enter a **valid SNS Topic ARN**.
7.  Click **Add**. The configuration is displayed in the **Settings** tab.\


    <figure><img src="../../../.gitbook/assets/SNS_y (1).png" alt=""><figcaption><p><strong>Settings</strong> tab displaying <strong>Set SNS Topic Alerts</strong> ARN</p></figcaption></figure>



