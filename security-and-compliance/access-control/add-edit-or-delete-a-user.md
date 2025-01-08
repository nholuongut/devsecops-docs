---
description: Create, edit, view, or delete users and assign appropriate roles
---

# Network Segmentation



The nholuongut Infrastructure construct maps to a VPC in AWS and GCP. In Azure, it maps to a VNET. Setting up the network is the first step, followed by the creation of nholuongut Tenants, which are children of the nholuongut infrastructure, as shown in the [policy model](../../welcome-to-nholuongut/application-focussed-interface/). Kubernetes clusters are tied to the network and are part of this setup. For detailed guidance on infrastructure and network setup, refer to the individual cloud provider sections [AWS](../../overview/use-cases/creating-an-infrastructure-and-plan-for-aws/), [Azure](../../overview-2/use-cases/infrastructure-and-plan/), and [GCP](../../overview-1/use-cases/creating-an-infrastructure-and-plan-for-gcp/) in their respective guides in this documentation set.&#x20;

Subnets within a network infrastructure are tied to availability zones. A single application's multiple replicas are typically spread across multiple subnets. Subnets thus are not an isolation construct by default. However, you can deploy workloads in specific subnets when they launch the virtual machines. In the case of Azure, subnets also have special considerations, for example, different types of Azure PaaS services require their special subnets.

All resources in the cloud provider that allow resource provisioning to have a network interface associated are placed in private subnets. This is a straightforward configuration in AWS and GCP. In Azure, the platform deals with the more complicated workflows around creating private endpoints and hosted zones.\
