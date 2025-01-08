---
description: Configure the kubectl shell for for nholuongut-managed GKE deployments
---

# Enable Kubectl Shell for GKE

Enabling `kubectl` shell access in GCP is part of a one-time nholuongut Portal setup process.

## Step 1: Create a Node Pool <a href="#step-1-create-a-node-pool" id="step-1-create-a-node-pool"></a>

1. In the **Tenant** list box, select the correct Tenant.
2. Navigate to **Kubernetes** -> **Nodes**.
3. Select the **Node Pool** tab, and click **Add.**

<figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FuExQuNr54zyRZQW9RqRZ%252Fnode%2520pool%2520new.png%3Falt%3Dmedia%26token%3D89012fcc-1ae5-4f38-b9ca-e27ccdac9d41&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=3d2cc22f&#x26;sv=1" alt=""><figcaption><p>The <strong>Add Node Pool</strong> pane</p></figcaption></figure>

4. Complete the required fields, and click **Create**. Once the node pool is complete, it will display on the **GCP VM** tab with a status of **Running**.

<figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FjnAVuFzguWeTXEEpkNje%252Fimage.png%3Falt%3Dmedia%26token%3Dea28b00f-0a8f-41fc-a22a-62347fe22f18&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=256a5d3d&#x26;sv=1" alt=""><figcaption><p>The <strong>GCE VM</strong> tab in the nholuongut Portal</p></figcaption></figure>

## Step 2. Create a nholuongut Service <a href="#step-2.-create-a-nholuongut-service" id="step-2.-create-a-nholuongut-service"></a>

1. In the **Tenant** list box, select the **correct** Tenant.
2. Navigate to **Kubernetes** -> **Services**.
3. Click **Add**. The **Add Service** page displays.
4. From the table below, enter the values that correspond to the fields on the **Add Service** page. Accept default values for fields not specified.

| Add Service page field | Value                                    |
| ---------------------- | ---------------------------------------- |
| **Name**               | `kubectl`                                |
| **Cloud**              | `Google`                                 |
| **Platform**           | `GKE Linux`                              |
| **Docker Image**       | `nholuongut/shell:terraform_kubectl_v15` |

5. In the **Environment Variables** field, enter the following YAML. Replace the flask app secret (b33d13ab-5b46-443d-a19d-asdfsd443 in this example) with a string of random numbers and letters in the same format and replace _**CUSTOMER\_PREFIX**_ with your customer URL prefix.

```
- Name: FLASK_APP_SECRET
 Value: b33d13ab-5b46-443d-a19d-asdfsd443
- Name: DUPLO_AUTH_URL
 Value: https://<CUSTOMER_PREFIX>.nholuongut.net
```

6. Click **Next**. The **Advanced Options** page displays.
7. Click **Create**. The Service is created.

## Step 3: Create a Load Balancer <a href="#step-3-create-a-load-balancer" id="step-3-create-a-load-balancer"></a>

1. Navigate to **Kubernetes** -> **Services**.
2. Select the **kubectl** Service from the **NAME** column.
3. Select the **Load Balancers** tab, and click **Configure Load Balancer**. The **Add Load Balancer Listener** pane displays.
4. In the **Select Type** list box, select **K8s Cluster IP**.
5. In the **Container port** and **External port** fields, enter **80**.
6. In the **Health Check** field, enter **/duplo\_auth**.
7. In the **Backend Protocol** list box, select **TCP**
8. Select **Advanced Kubernetes settings** and **Set HealthCheck annotations for Ingress.**
9. Click **Add**. The Load Balancer listener is added.

<div align="left"><figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FYubrSqkGFBjD8pOeXs5f%252Fnew%2520LB%2520pic.png%3Falt%3Dmedia%26token%3D89092ff1-99a2-4772-bf32-83254b0d219a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=9b57daeb&#x26;sv=1" alt="" width="375"><figcaption><p>The <strong>Add Load Balancer Listener</strong> pane</p></figcaption></figure></div>

## Step 4: Add an Ingress <a href="#step-4-add-an-ingress" id="step-4-add-an-ingress"></a>

1. In the **Tenant** list box, select the correct Tenant.
2. Navigate to **Kubernetes** -> **Ingress**.
3. Click **Add**. The **Add Kubernetes Ingress** page displays.
4. In the **Ingress Name** field, enter `kubect-shell`.
5. From the **Ingress Controller** list box, select **gce**.
6. In the **Visibility** list box, select **Public**.
7. In the **DNS Prefix** fiel&#x64;**,** enter the DNS name prefix.
8. In the **Certificate ARN** list box, select the ARN added to the Plan in the **Certificate for Load Balancer and Ingress** step.

<div align="left"><figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FJj2Od9HA2DlQfxc24HHR%252Fadd%2520ingress%2520new.png%3Falt%3Dmedia%26token%3D28b41a61-797b-4837-92d2-fa5ad8d4caa1&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=294a09de&#x26;sv=1" alt=""><figcaption><p>The <strong>Add Kubernetes Ingress</strong> page</p></figcaption></figure></div>

9. Click **Add Rule**. The **Add Ingress Rule** pane displays.
10. In the **Path** field, enter (**/**)
11. In the **Service Name** list box, select the Service previously created (**kubectl:80**)
12. Click **Add Rule**. A rule directing all traffic to the **kubectl** Service is created.

<div align="left"><figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FwzAO4oY0dSyy2QLYqGzd%252Fingress%2520newest.png%3Falt%3Dmedia%26token%3Deb45895e-25df-47fa-a2c2-03247c10ebd0&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ed174b16&#x26;sv=1" alt="" width="375"><figcaption><p>The <strong>Add Ingress Rule</strong> pane</p></figcaption></figure></div>

13\. On the **Add Kubernetes Ingress** page, click **Add**. The Ingress is created.

## Step 5: Add the DNS Name to System Settings <a href="#step-5-add-the-dns-name-to-system-settings" id="step-5-add-the-dns-name-to-system-settings"></a>

1. Navigate to **Administrator** -> **Systems Settings**.
2.  Select the **System Config** tab, and click **Add**. The **Add Config** pane displays.\


    <div align="left"><figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FzZCW2GzLSR4Eu5ONp4xV%252Fshrunk.png%3Falt%3Dmedia%26token%3De9588db4-41fd-4de2-9e0d-c702d7484dde&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=efefb027&#x26;sv=1" alt="" width="375"><figcaption><p>The <strong>Add Config</strong> pane</p></figcaption></figure></div>
3. From the **Config Type** list box, select **AppConfig**.
4. From the **Key** list box, select **Other**.
5. In the second **Key** field, enter **DuploShellfqdn**
6.  In the **Value** field, paste the Ingress DNS. To find the Ingress DNS, navigate to **Kubernetes** -> **Ingress**, and copy the DNS from the **DNS** column.



    <figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FdDMQmAFJQuKd5e9JdJPp%252Fimage.png%3Falt%3Dmedia%26token%3D9d66dafb-e876-4918-aa2e-ccbd0bbe2dde&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=9f82133d&#x26;sv=1" alt=""><figcaption></figcaption></figure>
7. Click **Submit**. `kubectl` shell access is enabled.
