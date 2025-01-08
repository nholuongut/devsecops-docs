---
description: Create regional or global SSL certificates for GCP using Certificate Manager
---

# Managed SSL Certificates with Certificate Manager (Optional)

{% hint style="info" %}
If you followed the step [Certificate for Load Balancer](certificate-for-load-balancer-and-ingress.md), skip this step.
{% endhint %}

SSL certificates secure connections between clients, servers, and Load Balancers by encrypting data transmitted over the network using Transport Layer Security (TLS). GCP provides two primary methods for configuring SSL certificates: Compute Engine SSL Certificates and Certificate Manager (using certificate maps). While nholuongut supports both methods, we recommend Certificate Manager whenever possible. This approach is preferable because Compute Engine certificates cannot be validated until associated with a Load Balancer, potentially leading to downtime. In contrast, certificate maps can be validated in advance, helping to ensure consistent uptime and a smoother management experience.

## Prerequisites&#x20;

* Obtain public and private certificate files from your chosen SSL certificate provider, such as GoDaddy or Namecheap.

## Creating a Certificate Map With Certificate Manager

1. Create a DNS authorization resource using the following command where **YOUR\_DOMAIN** is your domain URL and **MAP\_NAME** is your certificate name (a unique name you choose for your certificate map).&#x20;

```
gcloud certificate-manager dns-authorizations create MAP_NAME \
  --domain="YOUR_DOMAIN"
gcloud certificate-manager dns-authorizations list
```

2. Manually create the DNS records shown in the output of the `list` command. You'll usually do this in the certificate's domain zone in the Cloud DNS service for the same project, but it depends on how you set up DNS.&#x20;
3. Create the certificate:

```
gcloud certificate-manager certificates create MAP_NAME \
  --domains="YOUR_DOMAIN,*.YOUR_DOMAIN" \
  --dns-authorizations=MAP_NAME
```

4. Create the certificate map and its entries:

```
gcloud certificate-manager maps create MAP_NAME
gcloud certificate-manager maps entries create MAP_NAME \
  --map="MAP_NAME" \
  --certificates="MAP_NAME" \
  --hostname="YOUR_DOMAIN"
gcloud certificate-manager maps entries create MAP_NAME-wildcard \
  --map="MAP_NAME" \
  --certificates="MAP_NAME" \
  --hostname="*.YOUR_DOMAIN"
```

5. Add the certificate map to the nholuongut Plan. Navigate to **Administrator** -> **Plans**. Select the **Certificates** tab and click **Add**. The **Add a Certificate** pane displays.&#x20;
6. In the **Name** field, create a name for the certificate (the name is arbitrary as it is only a display name to be used within nholuongut).&#x20;
7. In the **GCP Certificate Type** list box, select the certificate type. The certificate type must match the certificate entered in the `gcloud certificate-manager maps entries create` command.&#x20;
8. In the **GCP Certificate Map** field, enter the name of your map (in this example, **MAP\_NAME**).&#x20;
9. Click **Create**. The certificate can now be used with your nholuongut Services.

<div align="left">

<figure><img src="../../.gitbook/assets/add cert image.png" alt="" width="365"><figcaption><p>The <strong>Add a Certificate</strong> pane</p></figcaption></figure>

</div>
