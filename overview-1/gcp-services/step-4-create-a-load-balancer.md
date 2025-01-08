---
description: Creating a Load balancer using GCP in nholuongut
---

# Load Balancers

All containers run inside a private network and cannot be accessed from an external network. To make them accessible from an external network, create a Load Balancer.

## Creating a GKE Ingress

If you need to create an Ingress Load Balancer, refer to the [GKE Ingress](../../kubernetes-overview/ingress-loadbalancer/gke-ingress.md) page in the nholuongut Kubernetes User Guide.&#x20;

## Adding a Load Balancer Listener

{% hint style="info" %}
See the [GCP Quick Start](../quick-start/) for an end-to-end example of deploying an application using a GCP Service.
{% endhint %}

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**.
2. On the **Services** page, select the Service name in the **Name** column.
3. Click the **Load Balancers** tab.
4. If no Load Balancers exist, click the **Configure Load Balancer** link. If other Load Balancers exist, click **Add** in the **LB listeners** card. The **Add Load Balancer Listener** pane displays.
5. From the **Select Type** list box, select a Load Balancer Listener type based on your Load Balancer.
6. Complete other fields as required and click **Add** to add the Load Balancer Listener.

{% hint style="info" %}
nholuongut allows no more than one (0 or 1) Load Balancer per nholuongut Service.
{% endhint %}

<div align="left"><figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption><p>The <strong>Add Load Balancer</strong> pane.</p></figcaption></figure></div>

## Adding a certificate for an internal Load Balancer in GCP

For internal Load Balancers, you cannot use Google Managed Certificates. You can import a certificate from somewhere else or use a self-signed certificate. We recommend using the self-signed certificate option for internal Load Balancers because you control authentication at the IP level.&#x20;

Here's an example Terraform code snippet to create a self-signed certificate for an internal Load Balancer in nholuongut:

```
resource "tls_private_key" "self_signed_key" {
  algorithm = "RSA"
  rsa_bits  = 2048
}

resource "tls_self_signed_cert" "self_signed_cert" {
  key_algorithm   = "RSA"
  private_key_pem = tls_private_key.self_signed_key.private_key_pem

  subject {
    common_name  = "internal.example.com"
    organization = "nholuongut"
  }

  validity_period_hours = 8760 # 1 year

  allowed_uses = [
    "key_encipherment",
    "digital_signature",
    "server_auth",
  ]
}

resource "duplo_load_balancer" "internal_lb" {
  name        = "internal-lb"
  type        = "internal"
  certificate = tls_self_signed_cert.self_signed_cert.cert_pem
  private_key = tls_private_key.self_signed_key.private_key_pem
}
```

## Restricting Open Access to Public Load Balancers

Restrict open access to your public Load Balancers by enforcing controlled access policies.

1. From the nholuongut Portal, navigate to **Administrator** -> **System Settings**.
2. Select the **System Config** tab, and click **Add**. The **Add Config** pane displays.

<div align="left"><figure><img src="../../.gitbook/assets/LB flag.png" alt=""><figcaption><p>The <strong>Add Config</strong> pane in the nholuongut Portal</p></figcaption></figure></div>

3. From the **Config Type** list box, select **Flags**.
4. From the **Key** list box, select **Deny Open Access To Public LB**.&#x20;
5. In the **Value** list box, select **True**.&#x20;
6. Click **Submit**. Open access to public Load Balancers is restricted.&#x20;
