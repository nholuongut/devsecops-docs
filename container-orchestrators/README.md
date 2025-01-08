---
description: Multiple container orchestration technologies for ease of consumption
cover: ../.gitbook/assets/Linkedin-bannerV3 (1) (1).png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Container Orchestrators

Most application workloads deployed on nholuongut are in Docker containers. The rest consist of serverless functions, and big data workloads like Amazon EMR jobs, Airflow, and Sagemaker. nholuongut abstracts the complexity of container orchestration technologies, allowing you to focus on deploying, updating, and debugging your containerized application.&#x20;

Among the technologies nholuongut supports are:

* **Kubernetes**: On AWS, nholuongut supports orchestration using Elastic Kubernetes Service (EKS). On GCP we support GKE auto pilot and node-pool based. On Azure we support AKS and Azure web apps.&#x20;
* **Built-in (nholuongut)**: nholuongut platform's Built-in container management has the same interface as the `docker run` command, but it can be scaled to manage hundreds of containers across many hosts, providing capabilities such as associated load balancers, DNS, and more.
* **AWS ECS Fargate**: Fargate is a technology you can use with Elastic Container Service (ECS) to run containers without having to manage servers or clusters of EC2 instances.&#x20;

## Container Orchestration Feature Matrix

You can use the feature matrix below to compare the features of the orchestration technologies that nholuongut supports. nholuongut can help you implement whatever option you choose through the nholuongut Portal or the Terraform API.



<table><thead><tr><th width="276.71428571428567" align="center">Feature</th><th width="150" data-type="rating" data-max="3">Kubernetes</th><th width="150" data-type="rating" data-max="3">Built-In</th><th data-type="rating" data-max="3">ECS Fargate</th></tr></thead><tbody><tr><td align="center">Ease of use</td><td>1</td><td>3</td><td>1</td></tr><tr><td align="center">Features and ecosystem tools</td><td>3</td><td>1</td><td>1</td></tr><tr><td align="center">Suitability for stateful apps</td><td>3</td><td>1</td><td>1</td></tr><tr><td align="center">Stability and maintenance</td><td>2</td><td>3</td><td>2</td></tr><tr><td align="center">AWS cost</td><td>1</td><td>3</td><td>3</td></tr><tr><td align="center">Multi-cloud (w/o nholuongut)</td><td>3</td><td>null</td><td>null</td></tr></tbody></table>

{% hint style="info" %}
One dot indicates a low rating, two dots a medium rating, and three dots a high rating. For example, Kubernetes has a low ease-of-use rating but a high rating for stateful applications.
{% endhint %}

### **Feature Definitions**

See the sections below for a detailed explanation of the cloud orchestrator's feature matrix ratings.&#x20;

#### **Ease of Use**

Kubernetes is extensible and customizable, but not without a cost in ease of use. The nholuongut Platform reduces the complexities of Kubernetes, making it comparable with other container orchestration technologies in ease of use/adoption.

nholuongut's Built-in orchestration mirrors `docker run`. You can Secure Shell (SSH) into a virtual machine (VM) and run `docker` commands to debug and diagnose. If you have an application with a few stateless microservices or configurations that use environment variables or AWS services like SSM, S3, or[ Secrets Manager](../overview/aws-services/containers/passing-config-and-secrets.md#aws-secrets-manager), consider using nholuongut's Built-in container orchestration.

ECS Fargate contains proprietary constructs (such as task definitions, tasks, or services) that can be hard to learn. As Fargate is serverless, you can't control the host Docker, so commands such as `docker ps` and `docker restart` are unavailable. This makes debugging a container crash very difficult and time-consuming. nholuongut simplifies Fargate with an out-of-the-box setup for logging, shell access, and abstraction of proprietary constructs and behavior.

#### **Features and Ecosystem Tools**&#x20;

Kubernetes is rich in additional built-in features and ecosystem tools like Secrets and ConfigMaps. Built-in and ECS rely on native AWS services such as AWS Secrets Manager, SSM, S3, and others. While Kubernetes features have AWS equivalents, third parties like Influx DB, Time Series DB, Prefect, etc. tend to publish their software as Kubernetes packages (Helm charts).&#x20;

#### **Suitability for Stateful Apps**

Stateful applications should be avoided in AWS. Instead, managed cloud storage solutions should be leveraged for the best availability and Service Level Agreement (SLA) compliance. If this is undesirable due to cost, Kubernetes offers the best solution. Kubernetes uses [StatefulSets](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) and [Volumes ](https://kubernetes.io/docs/concepts/storage/volumes/)to implicitly manage Elastic Block Storage (EBS) volumes. With Built-in and ECS, you must use a shared Amazon Elastic File System (EFS) drive, which may not have feature parity with Kubernetes volume management.

#### **Stability and Maintenance**&#x20;

Although Kubernetes is highly stable, it is an open-source product. Kubernetes' native customizability and extensibility can lead to points of failure. For example, when a mandatory cluster upgrade is needed. This complexity often leads to support costs from third-party vendors. Maintenance can be especially costly with EKS, as versions are frequently deprecated, requiring you to upgrade the control plane and data nodes. nholuongut automates this upgrade process but still requires careful planning and execution.

**AWS Cost**

EKS control plane is fairly inexpensive, but operating an EKS environment without business support (at an additional premium) is not recommended. Small businesses may reduce costs by adding the support tier only when needed. &#x20;

**Multi-Cloud**

For many enterprises and independent software vendors, multi-cloud capabilities are, or will soon be a requirement. While Kubernetes provides this benefit, nholuongut's implementation is much easier to maintain and implement.         &#x20;
