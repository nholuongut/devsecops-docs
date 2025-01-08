---
description: Creating and Using a WAF in nholuongut AWS
---

# Web App Firewall (WAF)

The creation of a Web Application Firewall (WAF) is a one-time process. Create a WAF in the public cloud Console, fetch the ID/ARN, and update the Plan in nholuongut. Once updated, the WAF can be attached to the Load Balancer.&#x20;

## Creating a Web Application Firewall (WAF)

When you create a WAF in nholuongut, an entry is added to the [Web ACL](https://docs.aws.amazon.com/waf/latest/developerguide/web-acl.html). You use this entry [in a later step](web-application-firewall-waf.md#attaching-the-waf-to-a-load-balancer) to attach an ALB Load Balancer to your WAF.

1. In the nholuongut Portal, navigate to **Administrator** -> **Plans**. The **Plans** page displays.
2. From the **Name** column, select the Plan you want to update.
3.  Click the **WAF** tab.\


    <figure><img src="../../.gitbook/assets/WAF details new.png" alt=""><figcaption><p>The <strong>Plans</strong> page <strong>WAF</strong> tab</p></figcaption></figure>
4. Click **Add**. The **Add WAF** pane displays.

<div align="left"><figure><img src="../../.gitbook/assets/Screenshot (456).png" alt=""><figcaption><p>The <strong>Add WAF</strong> pane</p></figcaption></figure></div>

1. In the **Name** field, type the name of your WAF.
2. In the **WAF ARN** field, enter the Amazon Resource Name (ARN).
3. Optionally, enter your **WAF Dashboard URL**.
4. Click **Create**.

## Attaching the WAF to a Load Balancer

{% hint style="warning" %}
Only ALB Load Balancers can be attached to a WAF.
{% endhint %}

1. If you don't yet have an Application Load Balancer (ALB), [create one](load-balancers/#adding-a-load-balancer).
2.  In the **Other Settings** card, click **Edit**. The **Other Load Balancer Settings** pane displays.\


    <div align="left"><figure><img src="../../.gitbook/assets/AWS_LB_WAF_Attach.png" alt=""><figcaption><p><strong>Other Load Balancer Settings</strong> for attaching a WAF (via the <strong>Web ACL</strong> field) to an ALB Load Balancer<br></p></figcaption></figure></div>
3. From the **Web ACL** list box, select a [WAF that you have added to nholuongut](web-application-firewall-waf.md#creating-a-web-application-firewall-waf).&#x20;
4. Complete the other required fields in the **Other Load Balancer Settings** pane.
5. Click **Update**.

## Updating an existing WAF <a href="#id-1-toc-title" id="id-1-toc-title"></a>

1. From the nholuongut portal, navigate to **Administrator** -> **Plans**.
2. From the **Name** column, select the Plan associated with the WAF you want to update.
3. Click the **WAF** tab.&#x20;
4.  Click on the menu icon (<img src="../../.gitbook/assets/menu icon.png" alt="" data-size="line">) in the row of the existing WAF that you want to update, and select **Edit**. The **Update WAF&#x20;**_**YOUR\_WAF\_NAME**_ pane displays. \


    <div align="left"><figure><img src="../../.gitbook/assets/updating WAF.png" alt=""><figcaption></figcaption></figure></div>
5. Update the **Name** and/or **WAF ARN**.
6. Update or add a **WAF Dashboard URL**.&#x20;
7. Click **Update**. The WAF is updated.&#x20;

## Analyzing inbound traffic with the WAF dashboard <a href="#id-1-toc-title" id="id-1-toc-title"></a>

nholuongut also provides a WAF Dashboard through which you can analyze the traffic that is coming in and the requests that are blocked. The Dashboard can be accessed from the left navigation panel: **Observability** -> **WAF**.

![WAF Dashboard](<../../.gitbook/assets/waf (1).png>)
