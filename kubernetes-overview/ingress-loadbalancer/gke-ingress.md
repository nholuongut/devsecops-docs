---
description: Adding an Ingress for nholuongut Google Cloud Platform Load Balancers
---

# GKE Ingress

GCP's Ingress Controller for GKE automatically manages traffic routing to Kubernetes services, integrating Kubernetes workloads with Google Cloud's load-balancing infrastructure. It simplifies external access to applications, handling SSL termination and global load distribution.

GCP offers its own Ingress Controller, specifically created for Google Kubernetes Engine (GKE), to seamlessly integrate Kubernetes services with Google Cloud's advanced load balancing features.

### Container-native load balancing with GKE Ingress

Container-native load balancing on Google Cloud Platform (GCP) allows Load Balancers to directly target Kubernetes Pods instead of using a node-based proxy. This approach improves performance by enabling more efficient routing, reducing latency by eliminating extra hops, and providing better health-checking capabilities.&#x20;

It leverages the network endpoint groups (NEGs) feature to ensure that traffic is directed to the appropriate container instances, enabling more granular and efficient load distribution for applications running on GKE.

<figure><img src="../../.gitbook/assets/image (315).png" alt="" width="563"><figcaption><p><strong>GKE Container Native Load Balancing</strong></p></figcaption></figure>

## Prerequisites

### Creating Tenants and Services

Before you can create an Ingress, you must create a nholuongut Tenant and Service. See the nholuongut GCP User Guide for steps on how to create [Tenants](https://docs.nholuongut.com/docs/overview-1/use-cases/tenant-environment) and [Services](https://docs.nholuongut.com/docs/overview-1/gcp-services/containers).

Once your Tenant and Service are deployed, you are ready to add and configure a Load Balancer listener.

### Adding a Load Balancer listener with Kubernetes ClusterIP

Add a Load Balancer listener that uses Kubernetes (K8s) ClusterIP. Kubernetes Health Check and probes are enabled by default. To specifically configure the settings for Health Check, select **Additional health check configs** when you add the Load Balancer.

1. In the nholuongut Portal, navigate **Kubernetes** -> **Services.**
2. On the **Services** page, select the Service name from the **NAME** column.
3. Click the **Load Balancers** tab.
4. Click **Configure Load Balancer**. The **Add Load Balancer Listener** pane appears.

<div align="left">

<figure><img src="../../.gitbook/assets/image (316).png" alt="" width="375"><figcaption><p><strong>Add Load Balancer Listener</strong> pane</p></figcaption></figure>

</div>

5. From the **Select Type** list box, select **K8s Cluster IP**.&#x20;
6. Enable **Advanced Kubernetes Settings** and **Set HealthCheck annotations for Ingress**, if needed. (This will add required annotations in Kubernetes Service to be recognized by the GKE Ingress Controller)
7. Click **Add**. The Load Balancer listener details display in the **Load Balancers** tab on the Service details page.&#x20;

<figure><img src="../../.gitbook/assets/image (317).png" alt=""><figcaption><p><strong>Load Balancers</strong> tab for <strong>nginx-test</strong> service</p></figcaption></figure>

### Creating a GCP Managed Certificate (optional)

To enable SSL, create a GCP-managed certificate resource in the application namespace.

```
apiVersion: networking.gke.io/v1
kind: ManagedCertificate
metadata:
  name: my-managed-cert
  namespace: duploservices-npdev04gke
spec:
  domains:
  - npdev04.nholuongut.net #your A record name in DNS
```

## Adding a Kubernetes Ingress

Once a Service and Load Balancer are deployed, add an Ingress:

1. Select **Kubernetes** -> **Ingress** from the navigation pane.
2. Click **Add**. The **Add Kubernetes Ingress** page displays.
3. Enter an **Ingress Name**.
4. From the **Ingress Controller** list box, select **GCE.**
5. From the **Visibility** list box, select **Internal Only** or **Public**.&#x20;
6. Enter your DNS prefix in the **DNS Prefix** field.
7.  Select your ARN from the **Certificate ARN** list box. \


    <figure><img src="../../.gitbook/assets/NEW INGRESS.png" alt=""><figcaption><p>The <strong>Add Kubernetes Ingress</strong> page </p></figcaption></figure>
8. If you have [created a GCP managed cert](gke-ingress.md#create-gcp-managed-certificate-optional)[ificate](gke-ingress.md#create-a-gcp-managed-certificate-optional), add the following annotations in the **Annotations** field to link the Ingress with your GCP-managed certificate

```
"networking.gke.io/managed-certificates" = "my-managed-cert",
"kubernetes.io/ingress.allow-http" = "false"
```

9. Enter labels in the **Labels** field, if required.&#x20;
10. Click **Add** to add the Ingress.&#x20;

{% hint style="warning" %}
To add a Kubernetes Ingress, you must define [rules ](https://kubernetes.io/docs/concepts/services-networking/ingress/#ingress-rules). Continue to the next section to add rules to Kubernetes Ingress and complete the Ingress setup.&#x20;
{% endhint %}

### Configuring Kubernetes Ingress rules

1. In the **Add Kubernetes Ingress** page, click **Add Rule**. The **Add Ingress Rule** pane displays.&#x20;

<div align="left">

<figure><img src="../../.gitbook/assets/image (319).png" alt="" width="375"><figcaption><p><strong>Add Ingress Rule</strong> pane</p></figcaption></figure>

</div>

2. Specify the **Path** (**/samplePath/** in the example).
3. Optionally, specify the **Path Type** and **Host**. In this example, we specify a **Path Type** of **Exact**. Clicking the Info Tip icon ( <img src="../../.gitbook/assets/info_tip_black (1).png" alt="" data-size="line"> ) provides more information for these optional fields.
4. From the **Service Name** list box, select the Service exposed through the K8S ClusterIP (**nginx-test** in the example). The **Container port** field is completed automatically.&#x20;
5. Click **Add Rule**. The rule displays on the Add Kubernetes Ingress page. Repeat the preceding steps to add additional rules.
6. Click **Add** to add the Kubernetes Ingress. The Ingress displays on the **Ingress** page.

<figure><img src="../../.gitbook/assets/image (321).png" alt=""><figcaption><p><strong>Ingress</strong> page displaying the added Ingress</p></figcaption></figure>

The Ingress creation will take a few minutes. Once the IP is attached to the Ingress, you are ready to use your path- or host-based routing defined via Ingress.

## Viewing Ingress

You can view the Ingresses you have created by navigating to **Kubernetes** -> **Ingres**s.&#x20;

<figure><img src="../../.gitbook/assets/image (322).png" alt=""><figcaption><p>The Kubernetes <strong>Ingress</strong> page showing the added Ingress</p></figcaption></figure>

