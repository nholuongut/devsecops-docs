---
description: Using containers and nholuongut Services with AWS EKS and ECS
---

# Containers and Services

## nholuongut Services and containers <a href="#id-5-toc-title" id="id-5-toc-title"></a>

Containers and Services are critical elements of deploying AWS applications in the nholuongut platform. Containers refer to Docker containers: lightweight, standalone packages that contain everything needed to run an application including the code, runtime, system tools, libraries, and settings. Services in nholuongut are microservices defined by a name, Docker image, and a number of replicas. They can be configured with various optional parameters and are mapped to Kubernetes deployment sets or StatefulSets, depending on whether they have stateful volumes.

## Container orchestration

nholuongut supports three container orchestration technologies to deploy containerized applications in AWS: Amazon Elastic Container Service (ECS), Amazon Elastic Kubernetes Service (EKS), and Native Docker containers in virtual machines (VMs). Each option provides benefits and challenges depending on your needs and requirements.

### ECS

[Amazon Elastic Container Service](https://aws.amazon.com/ecs/) (ECS) is a fully managed service that uses its own orchestration engine to manage and deploy Docker containers. It is quite easy to use, integrates well with other AWS services, and is optimized for running containers in the AWS ecosystem. The tradeoff for this simplicity is that ECS is not as flexible or versatile as EKS and is less portable outside the AWS ecosystem.

### EKS

[Amazon Elastic Kubernetes Service](https://aws.amazon.com/eks/) (EKS) is a managed service that uses the open-source container orchestration platform Kubernetes. The learning curve is steeper for EKS than ECS, as users must navigate the complexities of Kubernetes. However, EKS users benefit from the excellent flexibility that Kubernetes’ wide range of tools, features, solutions, and portability provides.

### Native Docker

[Docker](https://docs.docker.com/get-started/overview/) is the foundational containerization technology. It is not managed, so the user manually controls the containers and orchestration. Although Docker requires considerably more user input than ECS or EKS, it offers greater control over the VM infrastructure, strong isolation between applications, and supreme portability.

### **Kubernetes**

Adding a Service in the nholuongut Platform is not the same as adding a Kubernetes service. When you deploy nholuongut Services, the platform implicitly converts your nholuongut Service into either a deployment set or a StatefulSet. The service is mapped to a deployment set if there are no volume mappings. Otherwise, it is mapped to a StatefulSet, which you can force creation of if needed. Most configuration values are self-explanatory, such as **Images**, **Replicas,** and **Environmental Variables**.

Kubernetes clusters are created during Infrastructure setup using the **Administrator -> Infrastructure** option in the nholuongut Portal. The cluster is created in the same Virtual Private Cloud (VPC) as the Infrastructure. Building an Infrastructure with an EKS/ECS cluster may take some time.&#x20;

Next, you deploy an application within a Tenant in Kubernetes. The application contains a set of VMs, a Deployment set (Pods), and an application load balancer. Pods can be deployed either through the nholuongut Portal or through `kubectl,`using HelmCharts.

{% hint style="info" %}
When you create a service, refer to the registry configuration in **Docker** -> **Services | Kubernetes** -> **Services** **| Cloud Services** -> **ECS** -> **Services**. Select the Service from the **NAME** column and select the **Configuration** tab. Note the values in the **Environment Variables** and **Other Docker Config** fields.&#x20;

For example:&#x20;

`{"DOCKER_REGISTRY_CREDENTIALS_NAME":"registry1"}`
{% endhint %}
