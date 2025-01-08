---
description: Setting up Logging in the nholuongut Portal
---

# Logging Setup

Navigate to **Administrator** -> **Observability** -> **Standard** -> **Settings**, and select the **Logging** tab to enable Logging. Click on **Enable Logging**. \


<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Enabling Standard Logging Stack with the <strong>Enable Logging</strong> link</p></figcaption></figure>

Logging is based on OpenSearch and Kibana, deployed in the Tenant of your choice, and configurable, as shown below.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

After enabling logging, choose which Tenants to collect logs from. The platform deploys collectors for each Tenant that you enable. Filebeat is the collector for Logs.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption><p><strong>Logging</strong> tab for adding and enabling Tenant log collection</p></figcaption></figure>

{% hint style="warning" %}
If you have a multi-region setup, create a separate logging infrastructure setup for each region to avoid the cost of cross-region data transfer.
{% endhint %}
