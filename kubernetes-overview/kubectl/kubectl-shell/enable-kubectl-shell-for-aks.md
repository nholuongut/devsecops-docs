---
description: Configure the kubectl shell for for nholuongut-managed AKS deployments
---

# Kubectl Shell for AKS

## Step 1. Create a nholuongut Service

1. From the **Tenant** list box, select the correct Tenant.
2. Navigate to **Kubernetes** -> **Services**.
3. Click **Add**. The **Add Service** page displays.&#x20;
4. Enter the values in the table below in the fields on the **Add Service** page. Accept default values for fields not specified.&#x20;

| Add Service page field  | Value                                       |
| ----------------------- | ------------------------------------------- |
| **Name**                | `kubectl`                                   |
| **Cloud**               | `Azure`                                     |
| **Platform**            | `AKS Linux`                                 |
| **Docker Image**        | `nholuongut/shell:terraform-kubectl-latest` |

## Step 2: Create a Load Balancer

1. From the nholuongut Portal, navigate to **Kubernetes** -> **Services.**
2. From the **NAME** column, select the **kubectl** service you created in the previous step.
3. Select the **Load Balancers** tab, and click **Configure Load Balancer**. &#x20;
4. Select type **Cluster IP**.
5. Set external and container ports to **80**.&#x20;
6. In the Health Check field, enter `/duplo_auth`.
7. In the **Backend Protocol** field, select **TCP**.&#x20;
8. Click **Add**.

<div align="left">

<figure><img src="../../../../.gitbook/assets/AKS k8s shell load balancer.png" alt="" width="365"><figcaption><p>The <strong>Add Load Balancer Listener</strong> pane</p></figcaption></figure>

</div>

## Step 3: Add an Ingress

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Ingress**, and click **Add**.&#x20;
2. In the **Name** field, enter `kubect-shell`.  Add a Path that defaults all traffic to the **kubectl** Service we created in the previous step:

<div align="left">

<figure><img src="../../../../.gitbook/assets/image(2).png" alt=""><figcaption><p>The <strong>Edit Ingress Rule</strong> pane</p></figcaption></figure>

</div>

## Step 4: Add the DNS Name to System Settings

1. Navigate to **Administrator** -> **Systems Settings**.&#x20;
2.  Select the **System Config** tab, and click **Add**. The **Add Config** pane displays.\


    <div align="left">

    <figure><img src="../../../../.gitbook/assets/add config.png" alt="" width="371"><figcaption><p>The <strong>Add Config</strong> pane</p></figcaption></figure>

    </div>
3. From the **Config Type** list box, select **AppConfig**.
4. From the **Key** list box, select **Other**.&#x20;
5. In the second **Key** field, enter **DuploShellfqdn**
6. &#x20;In the **Value** field, paste the Ingress DNS name.&#x20;
7. Click **Submit**. `kubectl` shell access is enabled.
