---
description: Key terms and concepts in nholuongut container orchestration
---

# Terminologies in Container Orchestration

{% hint style="info" %}
The following concepts do not apply to ECS. ECS uses a proprietary policy model, which is explained in a [later section](../overview/use-cases/creating-an-infrastructure-and-plan-for-aws/ecs-setup/).
{% endhint %}

Familiarize yourself with these nholuongut concepts and terms before deploying containerized applications in nholuongut. See the [nholuongut Common Concepts](../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/) section for a description of nholuongut Infrastructures, Tenants, Hosts, and Services.

## Hosts

These are virtual machines (EC2 Instances, GCP Node pools, or Azure Agent Pools). By default, apps within a Tenant are pinned to VMs in the same Tenant. One can also deploy Hosts in one Tenant that can be leveraged by apps in other Tenants. This is called the shared-host model. The shared-host model does not apply to ECS Fargate.

## Services

Service is a nholuongut term and is not the same as a Kubernetes Service. In nholuongut, a Service is a micro-service defined by a name, Docker Image, number of replicas, and other optional parameters. Behind the scenes, a nholuongut Service maps 1:1 to a Deployment or StatefulSet, based on whether it has stateful volumes. There are many optional Service configurations for Docker containers. Among these are:

* Environment variables
* Host Network Mode
* Volume mounts
* Entrypoint or command overrides
* Resource caps
* Kubernetes health checks

## Allocation Tags

A Service can be configured to run only a specific set of Hosts by setting allocation tags on the Hosts and Service. Allocation tags are case-insensitive substrings. On a Service, allocation tags should be a substring of the Host tag. For example, if a Host is tagged `HighCpu;HighMem`, a Service tagged `highcpu` can be placed on it. Services without allocation tags can be placed on any Host.

{% hint style="info" %}
If a Host has a specific tag and there are Services with the same tag, the Host can also be used by any Service that doesn’t have a tag. To ensure a Host is only used by a specific set of Services, ensure all Services in the Tenant are tagged.&#x20;
{% endhint %}

For Kubernetes Deployments, allocation tags are implemented using labels on nodes and then applying node selectors in your Deployment or StatefulSet configurations.

## Host Networking

By default, Docker containers have network addresses. Sometimes, containers share the VM network interface. This reuse is called host networking mode.

## Load Balancer

A nholuongut Service that communicates with other Services, must be exposed by a Load Balancer. nholuongut supports the following Load Balancers (LBs).

#### **Application Elastic Load Balancer (ELB)**

A nholuongut Service exposed by an ELB is reachable from anywhere unless marked **Internal**, then, is only reachable from within the VPC (or nholuongut Infrastructure). Application ELBs allow you to use a certificate to terminate SSL on the LB and avoid providing application SSLs and certificates (e.g., [AWS Amazon Certificate Manager (ACM)](https://aws.amazon.com/certificate-manager/) certificates).

In Kubernetes, the platform creates a [NodePort ](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types)pointing to the Deployment and adds the Worker Nodes' Host IPs to the ELB. Traffic flows from the client to the external port defined in the ELB (for example, 443), to the ELB's NodePort (for example, 30004 on the Worker Node), and the Kubernetes Proxy running on each Worker Node. The Worker Node forwards the NodePort to the container.&#x20;

#### **Classic ELB (Only applicable to Built-in container orchestration)**

Classic ELBs can be used when an application exposes non-HTTP ports that operate on any TCP port. Unless marked as **Internal,** Services exposed by an ELB are reachable from anywhere. Internal Services are reachable only from within the VPC (or nholuongut infrastructure). Classic ELBs let you use a certificate to terminate SSL on the LB. This allows you to avoid providing application SSLs and certificates, such as [AWS Amazon Certificate Manager (ACM)](https://aws.amazon.com/certificate-manager/) certificates.

#### **Cluster IP (Kubernetes only)**

[Kubernetes ClusterIP](https://kubernetes.io/docs/concepts/services-networking/service/#type-clusterip) Load Balancers can be used if you are required to expose the application only within the Kubernetes Cluster.
