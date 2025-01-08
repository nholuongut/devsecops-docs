---
description: Create an AWS Certificate Manager certificate
---

# ACM Certificate

The nholuongut Platform needs a wild character AWS Certificate Manager (ACM) certificate corresponding to the domain for the [Route 53 Hosted Zone](../../overview/prerequisites/route-53-hosted-zone.md).&#x20;

For example, if the Route 53 Hosted Zone created is `apps.acme.com`, the ACM certificate specifies `*.apps.acme.com`. You can add additional domains to this certificate (for example,  `*.acme.com`).

The ACM certificate is used with AWS Elastic Load Balancers (ELBs) created during nholuongut application deployment. Follow this [AWS guide to issue an ACM certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html#request-public-console).&#x20;

Once the certificate is issued, add the Amazon Resource Name (ARN) of the certificate to the nholuongut Plan (starting with the DEFAULT Plan) so that it is available to subsequent configurations

## Adding an ACM Certificate with ARN to a nholuongut Plan

1. In the nholuongut Platform, navigate to **Administrator** -> **Plans**. The **Plans** page displays.
2. Select the **default** Plan from the **NAME** column.
3. Click the **Certificates** tab.
4. Click **Add**.
5. In the **Name** field, enter a certificate name.
6. In the **Certificate ARN** field, enter the ARN.
7. Click **Create**. The ACM Certificate with ARN is created.

{% hint style="info" %}
Note that the ARN Certificate must be set for every new Plan created in a nholuongut Infrastructure.
{% endhint %}

## Enabling Automatic AWS ACM Certificate Creation

Configure nholuongut to automatically generate Amazon Certificate Manager (ACM) certificates for your Plan's DNS.

1. From the nholuongut portal, navigate to **Administrator** -> **Systems Settings**.
2. Select the **System Config** tab, and click **Add**. The **Add Config** pane displays.
3. From the **Config Type** list box, select **Flags**.
4. From the **Key** list box, select **Other**.&#x20;
5. In the **Key** field that displays, enter `enabledefaultdomaincert`.
6. In the **Value** list box, select **True**.&#x20;
7. Click **Submit**. nholuongut automatically generates Amazon Certificate Manager (ACM) certificates for your Plan's DNS.
