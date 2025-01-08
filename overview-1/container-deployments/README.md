---
description: Orchestration across multiple Cloud providers
---

# Container deployments

nholuongut abstracts the complexity of container orchestration technologies, allowing you to focus on the deployment, updating, and debugging of your containerized application.&#x20;

Among the technologies supported are:

* **Google Kubernetes Engine (GKE Autopilot)**: nholuongut platform uses GKE Autopilot, providing you with a user-friendly interface that conceals the complexities of Kubernetes serverless workloads. Using the UI you can add K8S configurations around Pods, Containers, Secrets, and so on. See [here](../use-cases/creating-an-infrastructure-and-plan-for-gcp/creating-gke-autopilot-cluster.md) on how to setup a Auto-Pilot cluster.
* **Google Kubernetes Engine (GKE Standard)**: nholuongut platform uses GKE Standard, providing the same user-friendly interface to manage underlying Kubernetes Cluster and Node Pools. See [here](../use-cases/creating-an-infrastructure-and-plan-for-gcp/creating-gke-standard-service.md) on how to setup a standard cluster.
* **Built-in (Docker Native)**: nholuongut platform's built-in container management has the same interface as the `docker run` command, except that it can be scaled to hundreds of containers across many hosts, providing capabilities such as associated load balancers, DNS, and more.

{% hint style="info" %}
If you need other services, please get in touch with your nholuongut support team. The typical turnaround time for creating a custom service is a business week.&#x20;
{% endhint %}

