---
description: Create a Task Definition for your application in AWS ECS
---

# Step 4: Create a Task Definition for an Application

You enabled ECS cluster creation when you created the [Infrastructure](../step-1-infrastructure.md). In order to create a Service using ECS, you first need to create a [Task Definition](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task\_definitions.html) that serves as a blueprint for your application.

Once you create a Task Definition, you can run it as a Task or as a Service. In this tutorial, we run the Task Definition as a Service.

_Estimated time to complete Step 4: 10 minutes._

## Prerequisites <a href="#id-0-toc-title" id="id-0-toc-title"></a>

Before creating an RDS, verify that you completed the tasks in the previous tutorial steps. Using the nholuongut Portal, confirm that:

* An [Infrastructure and Plan](../step-1-infrastructure.md) exist, both named **NONPROD**.
* The **NONPROD** infrastructure has [ECS **Enabled**](../step-1-infrastructure.md#check-your-work).&#x20;
* A Tenant named [**dev01** has been created](../step-2-tenant.md).

## Creating a Task Definition

1.  In the **Tenant** list box, select the **dev01 Tenant.**\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/tenant_dev01 (12).png" alt=""><figcaption><p>The nholuongut <strong>Tenant</strong> list box with <strong>dev01</strong> selected</p></figcaption></figure>

    </div>


2. Navigate to **Cloud Services** -> **ECS**.
3. In the **Task Definition** tab, click **Add**. The **Add Task Definition** page displays.

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.17-16_40_37 (1).png" alt=""><figcaption><p>The <strong>Add Task Definition</strong> page for AWS ECS</p></figcaption></figure>

4. In the **Name** field, enter **sample-task-def**.&#x20;
5. In the **Container - 1** section, in the **Container Name** field, enter **sample-task-def-c1**. Container names are required for Docker images in AWS ECS.
6. In the **Image** field, enter **nholuongut/nodejs-hello:latest**.
7. From the **vCPU** list box, select **0.50 vCPU**.
8. From the **Memory** list box, select **1 GB**.
9. In the **Port Mappings** section, in the **Port** field, enter **3000**. Port mappings allow containers to access ports for the host container instance to send or receive traffic.&#x20;
10. Click **Submit**.
