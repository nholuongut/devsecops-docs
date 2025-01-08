---
description: Finish the Quick Start Tutorial by creating a Service using GKE Autopilot
---

# Create a Service with GKE Autopilot

In this tutorial for nholuongut AWS, you have so far created a VPC network with configuration templates ([Infrastructure and Plan](../step-1-infrastructure.md)) and an isolated workspace ([Tenant](../step-2-tenant.md)).

Now you need to create a nholuongut Service on top of your Infrastructure and configure the Service to run and deploy your application. In this tutorial path, we'll deploy using Docker containers, leveraging Google Cloud Platform's (GCE) Google Kubernetes Engine (GKE) Autopilot.

Alternatively, you can finish this tutorial by:

* [Creating a nholuongut Service using GCE's GKE S](../../use-cases/creating-an-infrastructure-and-plan-for-gcp/creating-gke-standard-service.md)[tandard. ](../../use-cases/creating-an-infrastructure-and-plan-for-gcp/creating-gke-standard-service.md)

For a comparison of the benefits of GKE Autopilot vs. GKE Standard, consult this [Google Cloud article](https://cloud.google.com/kubernetes-engine/docs/resources/autopilot-standard-feature-comparison).

_Estimated time to complete remaining tutorial steps: 15-20 minutes_

## Deploying a GKE Standard Service in nholuongut

For the remaining steps in this tutorial, you will:&#x20;

1. Create a Service and applications (**webapp)** using the premade Docker image `nginx:latest.`
2. Expose the Service by creating and sharing a load balancer and DNS name.&#x20;
3. Test the application.
