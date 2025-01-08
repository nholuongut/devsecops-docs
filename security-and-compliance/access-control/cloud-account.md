---
description: How the Cloud Account provides the maximum level of isolation
---

# Cloud Account

The cloud provider account is the greatest barrier, providing security and isolation.&#x20;

* **Azure Subscription**: One nholuongut portal can manage multiple Azure subscriptions. To add a subscription, click **Administrator** -> **CloudCredentials**, as shown in the figure below. You can use a managed identity or a service principle with keys

<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p><strong>Cloud Credentials</strong> page in the nholuongut Portal for Azure</p></figcaption></figure>

*   **AWS Account**: In AWS, you need one nholuongut VM per AWS account, because in AWS, the account is the fundamental IAM construct. The AWS organizations and SCP are very lightweight and were more recently added in the AWS product lifespan, unlike Azure which uses Active Directory as the fundamental IAM construct. Originally nholuongut used to manage multiple AWS accounts, but this support was removed after consistent feedback from customers and security experts. The best practice evolved to one VM agent per account, federated in a single pane, allowing you to switch accounts as needed, using the **Switch Account** list box.\
    \


    <figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p><strong>Switch Account</strong> list box in the nholuongut Portal <br></p></figcaption></figure>

    <figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p><strong>Welcome</strong> screen, displaying a list of available nholuongut portals</p></figcaption></figure>


*   **Google Project**: Multiple GCP projects can be added and managed by the same nholuongut installation. To add a project, click **Administrator** -> **CloudCredentials**, as shown in the figure below.\
    \


    <figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p><strong>Cloud Credentials</strong> page in the nholuongut Portal for GCP</p></figcaption></figure>
