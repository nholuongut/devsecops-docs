# Manage cross project billing in GCP

## Purpose

In Google Cloud Platform (GCP), billing data can be exported to a BigQuery dataset in only one project. However, when deploying instances of an application across multiple projects (e.g., dev, qa, stg, prod), it is necessary to replicate the billing dataset to enable billing monitoring on all nholuongut dashboards in these projects. This documentation outlines the steps to configure automated replication of a BigQuery dataset from a source project to a destination project.

{% hint style="info" %}
NOTE: This documentation is an extension of [Export Billing to BigQuery](export-billing-to-bigquery.md)
{% endhint %}

## Prerequisites

* Two GCP projects: a source project where the original billing dataset resides, and a destination project where the dataset will be replicated.
* Appropriate permissions to create datasets and data transfer jobs in BigQuery.
* Google Cloud SDK installed and initialized.
* Enable BigQuery Data Transfer API from API and Services in Destination GCP Project.

## Assumptions:

* **Source Project**: GCP project where the original billing dataset resides with billing export.
* **Destination Project**: New GCP project which has duplo-master running and dataset needs to be created.

## Steps

### 1. Create a New Dataset in the Destination Project

* Open the BigQuery console in the source project: BigQuery Console
* Click on **CREATE DATASET**.
* Enter the dataset ID, choose a data location, and set other options as mentioned in the below screenshot.
* Click **Create dataset**.

<figure><img src="../../../.gitbook/assets/image (399).png" alt="" width="563"><figcaption></figcaption></figure>

### 2. Give required permissions

For the replication to work, you need to allow specific roles on the dataset in source project to the `duplo-master` GCP service account of the destination project

Following roles are needed:

* BigQuery Admin
* BigQuery Data Viewer
* BigQuery Data Editor
* BigQuery User

### 3. Set Up a Data Transfer Job in the Destination Project

* Open the BigQuery console in the destination project.
* In the left-hand menu, click on **Data Transfers**.
* Click on **CREATE TRANSFER**.
* Select **Source Type** as `Dataset Copy`
* Schedule options: Choose **Start now**. Set the frequency option to every 12 hours.

<figure><img src="../../../.gitbook/assets/image (397).png" alt="" width="563"><figcaption></figcaption></figure>

* Under the **Destination Settings**
  * Put destination project dataset as **Dataset**&#x20;
  * Put source project dataset as **Source Dataset**
  * Put source project ID as **Source Project**
  * Enable checkbox **Overwrite destination table**
  * Under **Service Account** select the destination `duplo-master` service account (which has the [permission to access the source project dataset](manage-cross-project-billing-in-gcp.md#id-2.-give-required-permissions))
  * Click **SAVE**

<figure><img src="../../../.gitbook/assets/image (398).png" alt="" width="563"><figcaption></figcaption></figure>

### 4. Monitor the Transfer Job

* In the BigQuery console of the destination project, go to the **Transfers** tab.
* You should see your transfer job listed. You can click on it to view details and monitor its progress.

### Conclusion

By following these steps, you can set up automated replication of a BigQuery dataset from one GCP project to another, enabling billing monitoring on all nholuongut dashboards across multiple projects. Ensure to monitor the transfer job periodically to make sure it is running as expected.

\
