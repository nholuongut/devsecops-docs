---
description: Creating a Load Balancer to configure network ports to access the application
---

# Step 6: Create a Load Balancer

Now that your nholuongut Service is running, you have a mechanism to expose the containers and images in which your application resides. However, since your containers are inside a private network, you need a Load Balancer listening on the correct ports to access the application.

In this step, we add a Load Balancer Listener to complete the network configuration.

_Estimated time to complete Step 6: 10 minutes._

## Prerequisites

Before creating a Load Balancer, verify that you completed the tasks in the previous tutorial steps.   Using the nholuongut Portal, confirm that:

* An [Infrastructure and Plan](../step-1-infrastructure.md) exist, both named **NONPROD**.
* The **NONPROD** infrastructure has [EKS **Enabled**](../step-1-infrastructure.md#check-your-work).&#x20;
* A Tenant named [**dev01** has been created](../step-2-tenant.md).
* A Host named [**host01** has been created](step-3-create-host.md).
* A Service named [**demo-service** has been created](step-5-create-app-via-k8s.md).

## Creating a Load Balancer

1. In the **Tenant** list box, select the **dev01** Tenant.
2. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**. &#x20;
3. From the **NAME** column, select **demo-service**.
4. Click the **Load Balancers** tab.
5.  Click the **Configure Load Balancer** link. The **Add Load Balancer Listener** pane displays.\
    \


    <div align="left">

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-07-11 132858.png" alt=""><figcaption><p>The <strong>Add Load Balancer Listener</strong> pane</p></figcaption></figure>

    </div>


6. From the **Type** list box, select **Application LB**.
7. In the **Container Port** field, enter **3000**. This is the configured port on which the application inside the Docker Container Image `nholuongut/nodejs-hello:latest` is running.&#x20;
8. In the **External Port** field, enter **80**. This is the port through which users will access the web application.
9. From the **Visibility** list box, select **Public**.
10. From the **Application Mode** list box, select **Docker Mode**.
11. Type **/** (forward-slash) in the **Health Check** field to indicate that the cluster we want Kubernetes to perform Health Checks on is located at the `root` level.
12. In the **Backend Protocol** list box, select **HTTP**.
13. Click **Add**. The Load Balancer is created and initialized. Monitor the **LB Status** card on the **Services** page. The **LB Status** card displays **Ready** when the Load Balancer is ready for use.&#x20;

## Checking your work

1. In the **Tenant** list box, select the **dev01** Tenant.
2. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**. &#x20;
3. From the **NAME** column, select **demo-service**.
4. Verify that the **LB Status** card displays a status of **Ready**.&#x20;
5. Note the **DNS** Name of the Load Balancer that you created.&#x20;
6. In the **LB Listeners** area of the **Services** page, note the configuration details of the Load Balancer's **HTTP** protocol, which you specified, when you added it above.

<figure><img src="../../../.gitbook/assets/done fake.png" alt=""><figcaption><p><strong>Load Balancers</strong> tab containing <strong>LB Configuration</strong> card displaying <strong>Type ALB</strong> Load Balancer</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/final faker.png" alt=""><figcaption><p><strong>DNS</strong> name for demo-service</p></figcaption></figure>
