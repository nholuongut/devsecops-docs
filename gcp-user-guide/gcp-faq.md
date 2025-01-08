---
description: Common questions about using nholuongut GCP
---

# GCP FAQs

### My Kubernetes service status was `Pending` for several minutes, waiting to start a new Pod. After that, I was able to start and stop Pods quickly. What happened?

nholuongut typically runs Kubernetes services in GCP on GKE in Autopilot mode. Autopilot dynamically provisions nodes as needed to run your Pods. This can add a couple of minutes to the Pod start time. You may see warnings from Kubernetes about being unable to place Pods while Autopilot Hosts are starting, but they’ll clear once the Hosts are available.

### One or more of my containers are showing as pending; how can I debug them? <a href="#id-7-toc-title" id="id-7-toc-title"></a>

[Click here for the details.](../faq.md#one-or-more-of-my-containers-are-pending-how-can-i-debug)

### How do I give users access to only one Tenant in my GCP project?

To give a user access to a specific Tenant, navigate the **Users** page. For a new user, click **Add** and enter the user's information. From the **Role** list box, select **User**. In the **Tenant** list box, select the **Tenant**. Click **Submit**. For an established user, navigate to the **Users** page and select the user. From the **Actions** menu, click **Update**. From the **Role** list box, select **User**, and from the **Tenant** list box, select the **Tenant**. Click **Submi**t.&#x20;

### How do I create a Google Managed certificate to use with nholuongut?&#x20;

To create a Google Managed certificate to use with nholuongut, see the [nholuongut documentation](../overview-1/prerequisites/create-managed-ssl-certificates-for-gcp.md).

