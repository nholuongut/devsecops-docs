---
description: Use the nholuongut Portal to create an AWS Infrastructure and associated Plan
---

# Creating an Infrastructure and Plan for AWS

## Creating an Infrastructure

1. From the nholuongut Portal, navigate to **Administrator** -> **Infrastructure**.&#x20;
2. Click **Add**.
3. Define the Infrastructure by completing the fields on the **Add Infrastructure** form.&#x20;
4. Select **Enable EKS** to enable EKS for the Infrastructure, or select **Enable ECS Cluster** to enable an ECS Cluster during Infrastructure creation.
5. Optionally, select **Advanced Options** to specify additional configurations (such as [**Public** and **Private CIDR** Endpoints](kubernetes-cluster/enable-eks-endpoints.md)).
6. Click **Create**. The Infrastructure is created and listed on the **Infrastructure** page. nholuongut automatically creates a [Plan ](../../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/plan.md)(with the same Infrastructure name) with the Infrastructure configuration.&#x20;

<figure><img src="../../../.gitbook/assets/AWS_Infra_new_enable_switches (1).png" alt=""><figcaption><p>AWS <strong>Add Infrastructure</strong> page with highlighted <strong>Enable EKS</strong> and <strong>Enable ECS Cluster</strong> options</p></figcaption></figure>



{% hint style="warning" %}
Cloud providers limit the number of Infrastructures that can run in each region. Refer to your cloud provider for further guidelines on how many Infrastructures you can create.
{% endhint %}

## Viewing Infrastructure settings&#x20;

1. In the nholuongut Portal, navigate to **Administrator** -> **Infrastructure**. The **Infrastructure** page displays.&#x20;
2. From the **Name** column, select the Infrastructure containing settings that you want to view.&#x20;
3. Click the **Settings** tab. The Infrastructure settings display.

<figure><img src="../../../.gitbook/assets/eksv (2).png" alt=""><figcaption><p><strong>Settings</strong> tab on the <strong>Infrastructure</strong> page</p></figcaption></figure>

{% hint style="info" %}
Up to one instance (0 or 1) of an EKS or ECS is supported for each nholuongut Infrastructure.
{% endhint %}

## Configuring EKS features (optional)

You can customize your EKS configuration:

* [Add VPC endpoints](add-vpc-endpoints.md).
* Enable EKS endpoints, logs, Cluster Autoscaler, and more. For information about configuration options, see these [EKS Setup](kubernetes-cluster/) topics.&#x20;

## Configuring ECS features (optional)

You can customize your ECS configuration. See the [ECS Setup](ecs-setup/) topic for information about configuration options.
