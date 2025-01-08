---
description: Create Autoscaling Groups (ASG) with Spot Instances in the nholuongut platform
---

# Spot Instances

[Spot Instances](https://aws.amazon.com/tutorials/ec2-auto-scaling-spot-instances/) are spare capacity priced at a significant discount compared to On-Demand Instances. Users specify the maximum price (bid) they will pay per hour for a Spot Instance. The instance is launched if the current Spot price is below the user's bid. Since Spot Instances can be interrupted when spare capacity is unavailable, applications using Spot Instances must be fault-tolerant and able to handle interruptions.

{% hint style="info" %}
Spot Instances are only supported for Auto-scaling Groups (ASG) with EKS
{% endhint %}

## Enabling Spot Instances when Creating Autoscaling Groups

Follow the steps in the section [Creating Autoscaling Groups (ASG)](./#creating-autoscaling-groups-asg). Before clicking **Add**, Click the box to access **Advanced Options**. Enable **Use Spot Instances** and enter your bid, in dollars, in the **Maximum Spot Price** field.&#x20;

<div align="left">

<figure><img src="../../../../../.gitbook/assets/spot instances screen shot.png" alt=""><figcaption><p>The <strong>Add ASG</strong> page with <strong>Use Spot Instances</strong> enabled and a <strong>Maximum Spot Price</strong> entered. </p></figcaption></figure>

</div>

## Creating Services using Spot Instances

Follow the steps in [Creating Services using Autoscaling Groups](./#creating-services-using-autoscaling-groups). In the **Add Service** page, **Basic Options**, Select **Tolerate spot instances**.&#x20;

<div align="left">

<figure><img src="../../../../../.gitbook/assets/add service basic.png" alt=""><figcaption><p>The <strong>Add Service</strong> page with <strong>Tolerate spot instances</strong> enabled.</p></figcaption></figure>

</div>

Tolerations will be entered by default in the **Add Service** page, **Advanced Options, Other Container Config** field. &#x20;

<div align="left">

<figure><img src="../../../../../.gitbook/assets/replacement shot.png" alt=""><figcaption><p>The <strong>Add Service</strong> page, <strong>Advanced Options</strong>, with tolerations shown in the <strong>Other Container Config</strong> field.</p></figcaption></figure>

</div>

