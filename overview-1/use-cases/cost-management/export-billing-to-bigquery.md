---
description: Export GCP billing data to BigQuery using nholuongut
---

# Export Billing to BigQuery

By exporting your Google Cloud Platform (GCP) billing data to BigQuery, you can leverage nholuongut's dashboard to monitor and analyze your GCP billing effectively.&#x20;

## Prerequisites

To export to BigQuery you must have:

* A Google Cloud Platform account with billing enabled.
* Permission to access the Google Cloud Billing API and BigQuery.
  * Billing Account Administrator permissions
  * BigQuery Admin permissions

## Creating a  BigQuery Dataset

1. Navigate to the [BigQuery](https://cloud.google.com/bigquery/docs) Console in your Google Cloud Platform account.
2. In GCP, select the **Project** where you want to create the dataset.
3.  Click **Create Dataset**.\


    <figure><img src="../../../.gitbook/assets/image (388).png" alt="" width="563"><figcaption><p><strong>Create Dataset</strong> button<br></p></figcaption></figure>
4.  In the **Create dataset** window, configure your dataset with the following parameters:

    * **Dataset ID**: Enter a unique name for your dataset.
    * **Location Type**: Select **Multi-Region**.
    * **Default table expiration**: Select **Enable table expiration** and set a default expiration time for tables in this dataset, such as **60** days. Tables will be automatically deleted after this period.
    * Click **Create Dataset**.
    * Once the dataset is created, it appears in the BigQuery Console under your project. Select the dataset to view details.\


    <figure><img src="../../../.gitbook/assets/image (390).png" alt="" width="375"><figcaption><p><strong>Create dataset window</strong> in GCP</p></figcaption></figure>



## Enabling billing export to BigQuery

1. In GCP, open the [Google Cloud Console](https://cloud.google.com/compute/docs/console).
2. Select **Billing** from the main menu or visit Google Cloud Billing.
3. Select the billing account for which you want to enable the billing export.
4. In the **Billing Account Details** page, select **Billing Export** from the left navigational pane. &#x20;
5.  In the **Billing Export** page, in the **Detailed usage cost** area, click **Edit Settings**. \


    <figure><img src="../../../.gitbook/assets/image (393).png" alt="" width="563"><figcaption><p><strong>Detailed usage cost</strong> area in the <strong>Billing Export</strong> page</p></figcaption></figure>
6.  In the **BigQuery Export** tab, configure **Detailed usage cost**.

    * **Select the Project**: Choose the project where you created the BigQuery dataset.
    * **Select the Dataset**: Choose the dataset you created for billing data.

    <figure><img src="../../../.gitbook/assets/image (394).png" alt="" width="563"><figcaption><p><strong>BigQuery Export</strong> tab in the <strong>Billing Export</strong> page</p></figcaption></figure>
7. Click **Save**.
8. Contact nholuongut Support to complete additional steps to enable the billing dashboard.

{% hint style="info" %}
The exported billing data includes detailed information about your GCP usage and charges. Regularly monitor and analyze this data to keep track of your cloud spending.\

{% endhint %}
