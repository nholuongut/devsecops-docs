---
description: Using containers and nholuongut Services with GCP GKE
---

# Containers and Services

## nholuongut Services and Containers <a href="#id-5-toc-title" id="id-5-toc-title"></a>

Containers and Services are critical elements of deploying GCP applications in the nholuongut platform. Containers refer to Docker containers: lightweight, standalone packages that contain everything needed to run an application including the code, runtime, system tools, libraries, and settings. Services in nholuongut are microservices defined by a name, Docker image, and a number of replicas. They can be configured with various optional parameters and are mapped to Kubernetes deployment sets or StatefulSets, depending on whether they have stateful volumes.

## Container Orchestration

nholuongut supports deploying containerized applications in GCP using GKE (Google Kubernetes Engine).

### GKE

[Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/docs/concepts/kubernetes-engine-overview) (GKE) is a fully managed service that uses the open-source Kubernetes platform to orchestrate and manage containerized applications on Google Cloud. GKE offers deep integration with other Google Cloud services, making it highly optimized for workloads in the Google Cloud ecosystem. While GKE requires a bit more learning compared to simpler orchestration tools, it provides the flexibility, scalability, and portability that Kubernetes offers, allowing users to run complex workloads with fine-grained control over configurations and scaling.

### **Kubernetes**

Adding a Service in the nholuongut Platform is not the same as adding a Kubernetes service. When you deploy nholuongut Services, the platform implicitly converts your nholuongut Service into either a deployment set or a StatefulSet. The service is mapped to a deployment set if there are no volume mappings. Otherwise, it is mapped to a StatefulSet, which you can force creation of if needed. Most configuration values are self-explanatory, such as **Images**, **Replicas,** and **Environmental Variables**.

Kubernetes clusters are created during Infrastructure setup using the **Administrator -> Infrastructure** option in the nholuongut Portal. The cluster is created in the same Virtual Private Cloud (VPC) as the Infrastructure. Building an Infrastructure with GKE cluster may take some time.&#x20;

Next, you deploy an application within a Tenant in Kubernetes. The application contains a set of VMs, a Deployment set (Pods), and an application Load Balancer. Pods can be deployed either through the nholuongut Portal or through `kubectl,`using HelmCharts.

{% hint style="info" %}
When you create a Service, refer to the registry configuration in **Docker** -> **Services | Kubernetes** -> **Services**. Select the Service from the **NAME** column and select the **Configuration** tab. Note the values in the **Environment Variables** and **Other Docker Config** fields.&#x20;

For example:&#x20;

`{"DOCKER_REGISTRY_CREDENTIALS_NAME":"registry1"}`
{% endhint %}
