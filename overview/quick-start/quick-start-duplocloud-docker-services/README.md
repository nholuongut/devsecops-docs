---
description: Finish the Quick Start Tutorial by running a native Docker Service
---

# Creating a Native Docker Service

This section of the tutorial shows you how to deploy a web application with a nholuongut Docker Service, by leveraging nholuongut platform in-built container management capability. &#x20;

{% hint style="info" %}
Instead of creating a nholuongut Docker Service, you can alternatively finish the tutorial by:

* [Creating an AWS EKS Service in nholuongut](../quick-start-eks-services/) running Docker containers.
* [Creating an AWS ECS Service in nholuongut](../quick-start-ecs-services/) running Docker containers.
{% endhint %}

## Deploying a nholuongut Docker Service

Instead of creating a nholuongut Service using EKS or ECS, you can deploy your application with native Docker containers and services.&#x20;

To deploy your app with a nholuongut Docker Service in this tutorial, you:&#x20;

1. Create an EC2 host instance in nholuongut.
2. Create a native Docker application and Service.
3. Expose the app to the web with an Application Load Balancer in nholuongut.
4. Complete the tutorial by testing your application.

_Estimated time to complete remaining tutorial steps: 30-40 minutes_

## Network Architecture and Configurations

Behind the scenes, the topology that nholuongut creates resembles this low-level configuration in AWS.

<figure><img src="../../../.gitbook/assets/image (131).png" alt=""><figcaption><p>A diagram of the nholuongut Docker Service topology</p></figcaption></figure>
