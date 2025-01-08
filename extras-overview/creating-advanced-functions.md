---
description: Pin a container to a set of hosts using allocation tagging
coverY: 0
---

# Allocation Tagging

In nholuongut, allocation tags give you control over where containers and Services are deployed within a Kubernetes cluster. By default, nholuongut spreads container replicas across available Hosts to balance resource usage. Allocation tags allow you to label Hosts and Services with specific characteristics, capabilities, or preferences, and to "pin" Services to certain Hosts to meet your operational and resource needs. Allocation tags are useful for deployment requirements like using Hosts with specialized resources, meeting compliance standards, or isolating workloads.

{% hint style="warning" %}
For a Service to run on a specific Host, the Host and the Service must have matching allocation tags. Services without allocation tags are deployed on any available Host in the Kubernetes cluster.&#x20;
{% endhint %}

## Adding an Allocation Tag to a Host

Assign a tag describing the Host's characteristics or capabilities, such as resource capacity, geographic location, or compliance needs.&#x20;

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Hosts**. The **Hosts** page displays.
2. Select the Host from the **NAME** column. If the Host is part of an Auto-Scaling Group (ASG), select the **ASG** tab and select the correct ASG.
3. Click the **Allocation Tag** Edit Icon ( <img src="../.gitbook/assets/square_edit_icon (6).png" alt="" data-size="line">). The **Set Allocation Tag** pane displays.

<figure><img src="../.gitbook/assets/screenshot-nimbusweb.me-2024.02.20-15_29_49.png" alt=""><figcaption></figcaption></figure>

4. In the **Allocation Tag** field, enter a tag name. Use only alphanumeric characters. Hyphens ( **-** ) are supported as special characters if needed. For example, **highmemory-highcpu** is a valid tag name.
5.  Click **Set**. The allocation tag you set displays in the heading banner for the Host or ASG.\


    <figure><img src="../.gitbook/assets/AT2.png" alt=""><figcaption><p>The heading banner for an Auto-Scaling Group (ASG) with an allocation tag</p></figcaption></figure>

## Assigning an Allocation Tag to a Service

In the nholuongut Portal, navigate to the **Add Service** or **Edit Service** page, and enter a tag name in the **Allocation Tag** field. When the Service runs, nholuongut will attempt to select a Host with a matching allocation tag. To pin the Service to run on a specific Host, apply matching allocation tags to the Host and Service.&#x20;

## Editing or deleting an Allocation Tag

On the **Host** or **ASG** page, select the **Metadata** tab, and edit or delete the existing allocation tag.

