---
description: Implement GCP Cloud Armour in nholuongut
---

# Cloud Armour

GCP Cloud Armour helps protect your applications and websites against denial of service, web breaches, and cyber-attacks.&#x20;

Use nholuongut to activate your GCP Cloud Armour software and monitor your cloud infrastructures and deployed services and applications.

## Adding a Security Policy in the nholuongut Plan

Before you can use nholuongut with Cloud Armour, define a Security Policy in the nholuongut Plan that supports your nholuongut Infrastructure.

1. In the nholuongut Portal, navigate to **Administrator** -> **Plan**. The **Plans** page displays.
2. From the Name column, select the Plan that corresponds to your Infrastructure. When you create a nholuongut Infrastructure, a Plan is created with the same name.
3. Click the **Security Policy** tab.
4.  Click **Add**. The **Add Security Policy** pane displays.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/add-qa-deny-security-policy.png" alt=""><figcaption></figcaption></figure>

    </div>
5. In the **Name** field, enter an appropriate name for the Security Policy. This is the name used in the nholuongut portal. It is convenient to keep it the same as the **Security Policy ID**, but not required.
6. In the **Security Policy ID** field, enter the name of your GCP Cloud Armour Security Policy. This is the name used in the GCP console.
7.  Click **Create**. The Security Policy that you specified is displayed in the **Security Policy** tab.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/CA2.png" alt=""><figcaption><p><strong>Security Policy</strong> tab on the nholuongut <strong>Nonprod Plan</strong> page</p></figcaption></figure>

    </div>

## Adding the Cloud Armour Security Policy to a Load Balancer

Now that the Cloud Armour Security Policy has been defined in your nholuongut Plan, add the policy to a Load Balancer so that it can monitor network traffic.

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Services** or **Docker** -> **Services**.
2. Select the Service to which your Load Balancer is attached.
3. Click the **Load Balancer** tab.
4.  In the **Other Settings** card, click **Edit**. The **Other Load Balancer Settings** pane displays.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/CA3.png" alt=""><figcaption><p><strong>Other Load Balancer Settings</strong> pane with <strong>Security Policy</strong> selected</p></figcaption></figure>

    </div>
5. From the Security Policy list box, select the [Security Policy you added in the previous step](cloud-armour.md#adding-a-security-policy-in-the-nholuongut-plan).
6. Select the **Enable HTTP to HTTPS Redirect** option.
7. Select **Enable Access Logs** to view rule evaluations.
8. In the **Idle Timeout** field, enter the number of minutes for timeout, in seconds.
9. Click **Save**.&#x20;

The Security Policy displays in the Load Balancer's Other Settings card.

<div align="left">

<figure><img src="../../.gitbook/assets/CA4.png" alt=""><figcaption><p><strong>Other Settings</strong> card with <strong>Security Policy</strong> displayed</p></figcaption></figure>

</div>

## Modifying a Cloud Armour Configuration Security Policy

To change your Cloud Armour configuration to use a different security policy, edit the **Security Policy** in the nholuongut [Plan](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/plan.md#nholuongut-plans).

1. In the nholuongut Portal, navigate to **Administrator** -> **Plans**. The **Plans** page displays.
2. From the **Name** column, select the Plan that corresponds to your Infrastructure.
3.  Click the **Security Policy** tab.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/GCPS1.png" alt=""><figcaption><p>Plan <strong>Security Policy</strong> tab</p></figcaption></figure>

    </div>


4.  In the row listing your security policy, click the Edit Icon ( <img src="../../.gitbook/assets/square_edit_icon (5).png" alt="" data-size="line"> ) to change the Security Policy ID. The **Update Security Policy** pane displays.\


    <div align="left">

    <figure><img src="../../.gitbook/assets/GCPS2.png" alt=""><figcaption><p><strong>Update Security Policy</strong> pane</p></figcaption></figure>

    </div>


5. Modify the Security Policy **Name** and the **Security Policy ID** as appropriate.
6. Click **Update**. The changes are saved and displayed in the **Security Policy** tab.

## Viewing Security Policy logs

Logs will only be visible if you **Enable Access Logs** in the Load Balancer's Other Settings card.

To view Cloud Armor Security Policy logs:

1. Locate the Security Policy in the GCP Console.
2. Click the **Logs** tab.
3. Click the **View policy logs** link on the Logs tab to view logs of the policy's rule evaluations.

