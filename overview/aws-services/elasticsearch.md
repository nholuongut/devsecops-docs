---
description: Create an OpenSearch domain from the nholuongut portal
---

# OpenSearch

## Creating an OpenSearch domain

1. Navigate to **Cloud Services** -> **Analytics**, select the **OpenSearch** tab, and click the **Add** button. The **Add OpenSearch Domain** page displays.&#x20;
2. In the **Domain Name** field, create a name for the OpenSearch domain.
3. In the **OpenSearch Version** field, select the OpenSearch version you are using.
4. Select your needed instance size from the **Data Instance Size** list box.
5. Enter the the instance count in the **Data Instance Count** field, and choose the correct zone(s) from the **Zone** list box.
6. Optionally, enter a key in the **Encryption Key (Optional)** field.&#x20;
7. In the **Storage (In Gb)** field, enter the amount of storage needed.&#x20;
8. If needed, select a **Master Instance Count** and **Master Instance Size**.&#x20;
9. Use the toggle switches to enable encryption options (**Require SSL/HTTPS, Use Latest TLS Cipher,** or **Enable Node-to-Node Encryption**), if needed.

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.03.04-14_45_54.png" alt=""><figcaption><p>The <strong>Add OpenSearch Domain</strong> page.</p></figcaption></figure>

10. Optionally, use the toggle switch to **Enable UltraWarm data nodes** (nodes that are optimized for storing large volumes of data cost-effectively). When this option is enabled, additional fields display. Select a **Warm Instance type**, enter **Number of warm data nodes**, and **Enable Cold Storage** as your application requires.\


    <figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.27-14_39_49.png" alt=""><figcaption><p><strong>Enable UltraWarm data nodes</strong> selected, displaying additional options <strong>(Warm Instance type</strong>, <strong>Number of warm data nodes</strong>, and <strong>Enable Cold Storage</strong>)</p></figcaption></figure>
11. Click **Submit**. The OpenSearch domain is created.&#x20;

## Creating an OpenSearch domain without EBS storage

To create an OpenSearch without EBS storage, follow the steps to [create an OpenSearch domain](elasticsearch.md#creating-an-opensearch-domain). In the **Data Instance Size** list box, select **Other**, and enter a storage type instance, For example, `i3.2xlarge.search`. Complete the remaining steps and click **Submit**. &#x20;

<div align="left">

<figure><img src="../../.gitbook/assets/image (3) (2).png" alt=""><figcaption></figcaption></figure>

</div>

## Managing OpenSearch Logging

See the[ Logging documentation](../use-cases/central-logging/custom-log-collection.md).

