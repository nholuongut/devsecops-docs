---
description: Enable Cluster Autoscaler for a Kubernetes cluster
---

# Enable Cluster Autoscaler

### Configuring Cluster Autoscaler for your Infrastructure

The Cluster AutoScaler automatically adjusts the number of nodes in your cluster when Pods fail or are rescheduled onto other nodes.&#x20;

1. In the nholuongut Portal, navigate to **Administrator** -> **Infrastructure**. The **Infrastructure** page displays.
2. From the **NAME** column, select the Infrastructure with which you want to use Cluster AutoScaler.
3. Click the **Settings** tab.
4.  Click **Add**. The **Add Infra - Set Custom Data** pane displays.\


    <div align="left">

    <img src="../../../../.gitbook/assets/image (326).png" alt="Infra - Set Custom Data pane for Cluster Autoscaler">

    </div>


5. From the **Setting Name** list box, select **Cluster Autoscaler**.
6. Select **Enable** to enable EKS.
7.  Click **Set**. Your configuration is displayed in the **Settings** tab.\


    <figure><img src="../../../../.gitbook/assets/ASG.png" alt=""><figcaption><p><strong>Cluster Autoscaler</strong> configuraton enabled with <strong>Value true</strong></p></figcaption></figure>
