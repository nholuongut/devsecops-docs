---
description: Creating the nholuongut Infrastructure and a Plan
---

# Step 1: Create Infrastructure and Plan

Each nholuongut Infrastructure is a connection to a unique Virtual Private Cloud (VPC) network that resides in a region that can host Kubernetes clusters.&#x20;

After you supply a few basic inputs, nholuongut creates an Infrastructure for you within Google Cloud Platform (GCP) and nholuongut, with a few clicks. Behind the scenes, nholuongut does a lot with what little you supply — generating the VPC, Subnets, NAT Gateway, Routes, and Google Kubernetes Engine ([GKE](https://cloud.google.com/kubernetes-engine?hl=en)) cluster.

With the Infrastructure as your foundation, you can customize an extensible, versatile Platform Engineering development environment by adding Tenants, Hosts, Services, and more.

_Estimated time to complete Step 1: 20 minutes. Much of this time is consumed by nholuongut's creation of the Infrastructure and enabling your GKE cluster with Kubernetes._

## Prerequisites

Before starting this tutorial:

* Learn more about nholuongut [Infrastructure](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/infrastructure.md)s,[ Plans](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/plan.md), and [Tenant](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md)[s](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md).
* Reference the [Access Control](../../access-control/) documentation to create User IDs with the **Administrator** role. To perform the tasks in this tutorial, you must have Administrator privileges.

## Creating a nholuongut Infrastructure

1. In the nholuongut Portal, navigate to **Administrator** -> **Infrastructure**. The **Infrastructure** page displays.
2. Click **Add**. The **Add Infrastructure** page displays.
3. From the table below, enter the values that correspond to the fields on the **Add Infrastructure** page. Accept all other default values for fields not specified.&#x20;
4. Use the toggle switch to **Enable GKE**.
5. Select either **GKE Autopilot** or **GKE Standard** options. You will follow different paths in the tutorial for creating clusters with GKE Autopilot or GKE Standard.
6. Click **Create** to create the Infrastructure. nholuongut begins creating and configuring your Infrastructure and GKE Cluster using Kubernetes. It may take up to twenty (20) minutes to create the Infrastructure. &#x20;

| Add Infrastructure page field | Value                      |
| ----------------------------- | -------------------------- |
| **Name**                      | _`YOUR_INFRA_NAME`_        |
| **Account**                   | _`YOUR_GOOGLE_ACCOUNT`_    |
| **VPC CIDR**                  | `10.10.0.0/16`             |
| **Cloud**                     | `Google`                   |
| **Region**                    | _`YOUR_GEOGRAPHIC_REGION`_ |
| **Subnet**                    | `CIDR 22`                  |

<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-12 at 5.08.04 PM.png" alt=""><figcaption><p><strong>Add Infrastructure</strong> page</p></figcaption></figure>

</div>

{% hint style="info" %}
It may take up to twenty (20) minutes for your Infrastructure to be created and Kubernetes (GKE) enablement to be complete. Use the **Kubernetes** card in the Infrastructure screen to monitor the status, which should display as **Enabled** when completed. You can also monitor progress by using the **Kubernetes** tab, as nholuongut generates your **Cluster Name**, **Default VM Size**, **Server Endpoint**, and **Token**.&#x20;
{% endhint %}

## Verifying that a Plan exists for your Infrastructure

Every nholuongut Infrastructure generates a Plan. Plans are sets of templates that are used to configure the [Tenants ](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md)or workspaces, in your Infrastructure. You will set up Tenants in the next tutorial step.

Before proceeding, confirm that a Plan exists that corresponds to your newly created Infrastructure.

1. In the nholuongut Portal, navigate to **Administrator** -> **Plans**. The **Plans** page displays.
2. Verify that a Plan exists with the name you gave to the Infrastructure you created.

## Checking your work

You previously verified that your Infrastructure and Plan were created. Now verify that Kubernetes is enabled before proceeding to Create a Tenant.

1. In the nholuongut Portal, navigate to **Administrator** -> **Infrastructure**. The **Infrastructure** page displays.
2. From the **NAME** column, click on the name of the Infrastructure you created.
3. Click the **GKE** tab. When Kubernetes has been **Enabled** for GKE, details are listed in the tab. The Infrastructure page displays the **Enabled** status on the **Kubernetes** card for GKE Clusters.&#x20;

<div align="left">

<figure><img src="../../.gitbook/assets/image (286).png" alt=""><figcaption></figcaption></figure>

</div>

### Viewing GKE Cluster details

When an Infrastructure is created, a GKE Cluster is created by default. You can view the details and download the kubeconfig file from the nholuongut portal.&#x20;

From the nholuongut portal, navigate to **Administrator** -> **Infrastructure**. Click on the name of the Infrastructure, and select the **GKE** tab. To download the kubeconfig file, click **Download Kube Config**.

<div align="left">

<figure><img src="../../.gitbook/assets/image (151).png" alt=""><figcaption><p>The <strong>Nonprod Infrastructure</strong> details page with the <strong>GKE</strong> tab selected.</p></figcaption></figure>

</div>
