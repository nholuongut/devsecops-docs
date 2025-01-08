---
description: >-
  Use the nholuongut Portal to create an Infrastructure and associated Plan for
  GCP
---

# Creating an Infrastructure and Plan for GCP

## Creating an Infrastructure

{% hint style="warning" %}
Up to one (0 or 1) GKS instance is supported for each nholuongut Infrastructure.
{% endhint %}

1. Click **Administrator** -> **Infrastructure** from the navigation menu.&#x20;
2. Click **Add**.&#x20;
3. Complete the fields on the **Add Infrastructure** form to define the infrastructure.&#x20;
4. Optionally, click **Enable GKE** and complete the additional fields to create a **GKE Autopilot** or **Standard Cluster**.&#x20;
5. Click **Create**. The Infrastructure is created and is listed on the **Infrastructure** page. nholuongut automatically creates a Plan with the same name and configuration as the Infrastructure.

{% hint style="info" %}
Cloud providers limit the number of Infrastructures that can run in each region. If you have completed the steps to create an Infrastructure and it doesn't show a status of **Complete**, try selecting a different region.
{% endhint %}
