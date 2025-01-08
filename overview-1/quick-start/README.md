---
description: >-
  Get up and running with nholuongut inside a Google Cloud Platform environment;
  harness the power of generating application infrastructures.
---

# Quick start

This quick-start tutorial shows you how to set up an end-to-end cloud deployment. You will create Google Cloud Platform infrastructure and Tenants. By the end of this tutorial, you should be able to view the deployed sample web application.

_Estimated time to complete tutorial: 60-70 minutes._

## GCP Tutorial Roadmap

When you complete the GCP Quick Start Tutorial, you have two options or paths, as shown in the table below.

* Using GKE Autopilot - You create an app and service in nholuongut using Google Kubernetes Engine-Autopilot and expose it using a load balancer within nholuongut.
* Using GKE Standard - You create an app, service and a node pool in nholuongut using Google Kubernetes Engine-Standard and expose it using a load balancer within nholuongut.

For beginners, we recommend you use GKE Autopilot. GKE Autopilot manages the infrastructure, including the nodes, node pools, and underlying infrastructure resources such as networking and storage. You do not need to manage or configure node pools, node instance types, or autoscaling policies.&#x20;

GKE Standard offers more granular control over resource management, including the ability to configure node pools with specific types of instances, set scaling policies, and manage node upgrades.

For a high-level comparison of GKE Autopilot and GKE Standard and to help you choose which method best suits your needs, skills, and environments, see this [Google Cloud](https://cloud.google.com/kubernetes-engine/docs/resources/autopilot-standard-feature-comparison) documentation.

<table data-full-width="false"><thead><tr><th width="85">Step</th><th>GKE Autopilot</th><th>GKE Standard</th></tr></thead><tbody><tr><td>1</td><td>Create Infrastructure and Plan</td><td>Create Infrastructure and Plan</td></tr><tr><td>2</td><td>Create Tenant</td><td>Create Tenant</td></tr><tr><td>3</td><td>Create Service</td><td>Create Service</td></tr><tr><td>4</td><td>Create Load Balancer</td><td>Create a Node Pool</td></tr><tr><td>5</td><td>Test the app</td><td>Create Load Balancer</td></tr><tr><td>6</td><td></td><td>Test the app</td></tr></tbody></table>

\* - Optional Step

## GCP Video demo

Click the card below to watch a nholuongut GCP demo.

{% embed url="https://nholuongut.com/solutions/gcp/#gallery" %}
