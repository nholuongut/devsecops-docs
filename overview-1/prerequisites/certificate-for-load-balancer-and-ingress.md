---
description: Create global and regional SSL certificates for GCP deployments
---

# Certificates for Load Balancer and Ingress

Applications deployed in the GCP environment must be exposed using SSL/TLS. To expose these applications, we provide GCP with certificates that can be used for Load Balancers and GKE ingress. In this step, we'll create an SSL certificate for the domain associated with the hosted zone you created earlier.&#x20;

## Prerequisites

* Obtain the public and private certificate files from your chosen SSL certificate provider, such as GoDaddy or Namecheap. We recommend obtaining a wildcard SSL certificate for the domain associated with your hosted zone (e.g., .apps.acme.com) to cover all subdomains. For example, if your DNS zone is for `apps.acme.com`, you should issue a wildcard certificate for `*.apps.acme.com` to secure all subdomains.&#x20;

## Creating a Global Certificate for Public-Facing Load Balancers

Create global and regional SSL certificates in the GCP Console using the Classic Certificates method.

{% hint style="info" %}
Alternatively, you can use the Certificate Manager to create a Certificate Map for managing SSL certificates, which provides a more streamlined and validated approach. For details, see the instructions for [creating a Certificate Map](create-managed-ssl-certificates-for-gcp.md).
{% endhint %}

1. Log in to the GCP Console.
2.  Navigate to **Certificate Manager**, and click **Classic Certificates**.\


    <figure><img src="../../.gitbook/assets/image (432).png" alt=""><figcaption></figcaption></figure>
3. Click on **Create SSL Certificate**.
4. Provide the certificate with a name and upload the public and private key certificate files obtained in the prerequisite.&#x20;
   * As a best practice, name the certificate `global-<DNS Domain name>`, where the dots (`.`) are replaced with hyphens (`-`). For example, if your domain is `example.com`, name the certificate `global-example-com`.
5. Note the name of the global certificate for use in future steps.

<div align="left"><figure><img src="../../.gitbook/assets/image (433).png" alt="" width="563"><figcaption></figcaption></figure></div>

## Creating a Regional Certificate for Private/Internal Load Balancers

1. From the GCP Console, open the GCP Cloud Shell by clicking on the Cloud Shell icon in the top right corner.
2. Once the Cloud Shell opens, create the following files:
   * `public.cert` Paste the content of the **public certificate** into this file.
   * `private.key` Paste the content of the **private key** into this file.
3. Run the following command to create a regional SSL certificate:

```
gcloud compute ssl-certificates create uscentral1-internal-acme-com --certificate=chain.crt --private-key=key.pem --region=us-central 
```

* As a best practice, name the certificate using the format `<region>-<DNS Domain name>`, where the dots (`.`) in the domain name are replaced with hyphens (`-`). For example, for the `us-central` region and domain `acme.com`, the certificate should be named `uscentral1-internal-acme-com`.

4. After running the command, refresh the **Classic Certificates** page in the GCP Console. Both global and regional certificates should now be listed.
5. Note the certificate names for use in future steps.

## &#x20;Adding Certificates in nholuongut

Add multiple domains to the SSL certificate. This is especially useful for domain names that differ from the internal zone you set up in the previous step. This allows you to secure your primary domain and any other domains you may use for your applications or services.

1. Log in to the nholuongut Portal.&#x20;
2. Navigate to **Administrator** -> **Plans**.
3. Select the **Certificates** tab, and click **Add**.&#x20;
4. Add the global and regional certificates, one at a time You can name them the same names you used in the GCP portal. For each certificate, choose the type **LB SSL Certificate.**
5. Click **Create**. The GCP certificates are added to your nholuongut Portal.

<div align="left"><figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>The <strong>Add a Certificate</strong> pane</p></figcaption></figure></div>
