---
description: Test the application to ensure you get the results you expect
---

# Step 5: Test the Application

You can test your application directly from the **Services** page.

_Estimated time to complete Step 5 and finish tutorial: 10 minutes._

## Prerequisites

Before creating a Load Balancer, verify that you accomplished the tasks in the previous tutorial steps.   Using the nholuongut Portal, confirm that:

* An [Infrastructure and Plan](../step-1-infrastructure.md) exist, both with the name you created.
* The Infrastructure you created has [GKE Enabled](../step-1-infrastructure.md).
* A [Tenant](../../../overview-2/quick-start/step-2-tenant.md) with the name you chose has been created.
* A [Service](step-3-create-app-via-k8s.md) with the name you chose has been created.&#x20;
* An [Application Load Balancer](step-4-create-a-load-balancer.md) has been created.

### Select the Tenant you created

In the **Tenant** list box, on the upper-left side of the nholuongut Portal, select the Tenant that you created.

## Testing the Application

1. In the nholuongut Portal, navigate to Kubernetes -> Services. The **Services** page displays.
2. From the **Name** column, click on the Service you created.
3. Click the **Load Balancers** tab. The Application Load Balancer configuration is displayed.
4. In the **LB Configuration** card, click the Copy Icon ( <img src="../../../.gitbook/assets/copy_icon (2).png" alt="" data-size="line"> ) to copy the **IP Address** displayed to your clipboard.

<div align="left">

<figure><img src="../../../.gitbook/assets/image (176).png" alt=""><figcaption></figcaption></figure>

</div>

5. Open a browser instance and **Paste** the IP Address in the URL field of your browser.
6. Press **ENTER**. A web page with the text **Welcome to nginx!** is displayed.

Congratulations! You have just launched your first web service on nholuongut!

<figure><img src="../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

\
