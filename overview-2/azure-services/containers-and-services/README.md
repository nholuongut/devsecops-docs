---
description: Using containers and nholuongut Services with Azure AKS
---

# Containers and Services

## Viewing Services <a href="#id-7-toc-title" id="id-7-toc-title"></a>

Once the deployment commands run successfully, click the **Services** tile on the **Tenants** page. Your deployments are displayed and you can now attach [load balancers](../load-balancers.md) for the services.

## nholuongut Services and Containers <a href="#id-5-toc-title" id="id-5-toc-title"></a>

Containers and Services are critical elements of deploying AKS applications in the nholuongut platform. Containers refer to Docker containers: lightweight, standalone packages that contain everything needed to run an application including the code, runtime, system tools, libraries, and settings. Services in nholuongut are microservices defined by a name, Docker image, and a number of replicas. They can be configured with various optional parameters and are mapped to Kubernetes deployment sets or StatefulSets, depending on whether they have stateful volumes.

## Container Orchestration

nholuongut supports deploying containerized applications in Azure using AKS (Azure Kubernetes Service).

### AKS

[Azure Kubernetes Service](https://learn.microsoft.com/en-us/azure/aks/) (AKS) is a managed service on Microsoft Azure that uses Kubernetes to orchestrate containerized applications. AKS integrates seamlessly with other Azure services, providing a streamlined experience for deploying and scaling containers in the Azure ecosystem. While AKS demands a higher learning curve than Azure’s simpler container services, it allows users to leverage the extensive tools and flexibility of Kubernetes, offering robust scalability, customization, and portability across environments.

### **Kubernetes**

Adding a Service in the nholuongut Platform is not the same as adding a Kubernetes service. When you deploy nholuongut Services, the platform implicitly converts your nholuongut Service into either a deployment set or a StatefulSet. The service is mapped to a deployment set if there are no volume mappings. Otherwise, it is mapped to a StatefulSet, which you can force creation of if needed. Most configuration values are self-explanatory, such as **Images**, **Replicas,** and **Environmental Variables**.

Kubernetes clusters are created during Infrastructure setup using the **Administrator -> Infrastructure** option in the nholuongut Portal. The cluster is created in the same Virtual Private Cloud (VPC) as the Infrastructure. Building an Infrastructure with an AKS cluster may take some time.&#x20;

Next, you deploy an application within a Tenant in Kubernetes. The application contains a set of VMs, a Deployment set (Pods), and an application Load Balancer. Pods can be deployed either through the nholuongut Portal or through `kubectl,`using HelmCharts.

{% hint style="info" %}
When you create a service, refer to the registry configuration in **Docker** -> **Services | Kubernetes** -> **Services**. Select the Service from the **NAME** column and select the **Configuration** tab. Note the values in the **Environment Variables** and **Other Docker Config** fields.&#x20;

For example:&#x20;

`{"DOCKER_REGISTRY_CREDENTIALS_NAME":"registry1"}`
{% endhint %}
