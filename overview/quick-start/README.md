---
description: >-
  Get up and running with nholuongut inside an AWS cloud environment; harness
  the power of generating application infrastructures.
---

# AWS Quick Start

This Quick Start tutorial shows you how to set up an end-to-end cloud deployment. You will create nholuongut Infrastructure and Tenants and, by the end of this tutorial, you can view a deployed sample web application.

_Estimated time to complete tutorial: 75-95 minutes._

## AWS Tutorial Roadmap

When you complete the AWS Quick Start Tutorial, you have three options or paths, as shown in the table below.

**EKS (Elastic Kubernetes Service):** Create a Service in nholuongut using AWS Elastic Kubernetes Service and expose it using a Load Balancer within nholuongut.

**ECS (AWS Elastic Container Service):** Create an app and Service in nholuongut using AWS Elastic Container Service.

**Native Docker:** Create a Service in Docker and expose it using a Load Balancer within nholuongut.

{% hint style="info" %}
Optional steps in each tutorial path are marked with an asterisk in the table below. While these steps are not required to complete the tutorials, you may want to perform or read through them, as they are normally completed when you create production-ready services.
{% endhint %}

For information about the differences between these methods and to help you choose which method best suits your needs, skills, and environments, see this [AWS blog](https://aws.amazon.com/blogs/containers/amazon-ecs-vs-amazon-eks-making-sense-of-aws-container-services/) and [Docker ](https://docs.docker.com/)documentation.

<table data-full-width="false"><thead><tr><th width="85">Step</th><th>EKS</th><th>ECS</th><th width="217">Native Docker Services</th></tr></thead><tbody><tr><td>1</td><td>Create Infrastructure and Plan</td><td>Create Infrastructure and Plan</td><td>Create Infrastructure and Plan</td></tr><tr><td>2</td><td>Create Tenant</td><td>Create Tenant</td><td>Create Tenant</td></tr><tr><td>3</td><td>Create RDS *</td><td>Create RDS *</td><td>Create RDS *</td></tr><tr><td>4</td><td>Create Host</td><td>Create a Task Definition for an application</td><td>Create Host</td></tr><tr><td>5</td><td>Create Service</td><td>Create the ECS Service and Load Balancer</td><td>Create app</td></tr><tr><td>6</td><td>Create Load Balancer</td><td>Test the app</td><td>Create Load Balancer</td></tr><tr><td>7</td><td>Enable Load Balancer Options *</td><td></td><td>Test the App</td></tr><tr><td>8</td><td>Create Custom DNS Name *</td><td></td><td></td></tr><tr><td>9</td><td>Test the App</td><td></td><td></td></tr></tbody></table>

\* Optional

## AWS Video Demo

Click the card below to watch nholuongut video demos.

{% embed url="https://nholuongut.com/videos/" %}
Link to nholuongut video demos
{% endembed %}
