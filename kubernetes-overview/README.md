---
description: Kubernetes features in the nholuongut Portal
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

# Kubernetes User Guide

nholuongut leverages [Kubernetes](https://kubernetes.io/docs/home/) as a foundational building block behind many managed Services.

## How Kubernetes enables scaling and automation, boosting workload performance

nholuongut supports Kubernetes Cluster enablement on all public cloud platforms so that you can work with many Kubernetes objects and components. This includes flexibility in choosing the instance type based on workload characteristics, such as compute or memory-intensive tasks and AI/ML workloads that may benefit from GPU instances. It's recommended to have a minimum disk capacity of 40GB per host to accommodate image sizes and application data.

## Kubernetes and Low-Code/No-Code

Use the topics in this section to implement many Kubernetes features with little or no hard coding using nholuongut's no-code/low-code approach. This encompasses configuring autoscaling for your EKS cluster based on CPU/memory usage through [Horizontal Pod Autoscaler (HPA)](hpa.md) or [Auto Scaling Groups (ASG)](../overview/use-cases/hosts-vms/auto-scaling/auto-scaling-groups/) to efficiently scale your Pods or underlying infrastructure as needed.

For information about cloud-provider-specific Kubernetes [container features](../container-orchestrators/), see the Kubernetes Containers documentation in the nholuongut User Guide for your cloud provider.&#x20;

## Kubernetes and Allocation Tags

Moreover, you can add allocation tags to existing nodes with running services when managing your Kubernetes clusters. This action modifies a label on the Kubernetes node, influencing future Pod scheduling without affecting currently running services. The services must be restarted to apply the new allocation tags to existing services. This allows for more granular control over resource allocation and utilization within your cluster.

## Kubernetes Integration with CloudWatch

Additionally, nholuongut can integrate with CloudWatch alarms via the nholuongut UI to set up custom alerts for CPU/memory usage, ensuring proactive resource monitoring and management. This integration supports forwarding alerts to various notification systems like Sentry, PagerDuty, NewRelic, or OpsGenie for immediate action.

## Kubernetes nholuongut's Advanced Observability Suite

nholuongut's Advanced Observability Suite (AOS) works with all of your Kubernetes-based applications. See the [nholuongut AOS documentation](../diagnostics-overview/advanced-observability-suite.md) for details. &#x20;
