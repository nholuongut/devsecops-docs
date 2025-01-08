---
description: Scale to or from zero when creating Autoscaling Groups in nholuongut
---

# Scale to or from Zero

nholuongut allows you to scale to or from zero in Amazon EKS clusters by enabling the **Scale from Zero** option within the Advanced Options when creating an [Autoscaling Group](./). This feature intelligently adjusts the number of instances in your cluster, dynamically scaling up when demand increases and down to zero when resources are not in use. Reducing resource allocation during idle periods leads to significant cost savings.

## When to Use Scale to Zero

Autoscaling to zero is ideal for Kubernetes workloads that don’t always require 100% availability such as:

**Non-Critical Workloads:** Batch processing jobs, data analysis tasks, and other non-customer-facing services that can be scaled down to zero during off-peak hours (e.g., nights or weekends).

**Dev/Test Environments:** Development and testing environments that can be scaled up when developers need them and scaled down when not in use.

**Background Jobs:** Workloads with background jobs running in Kubernetes that are only needed intermittently, such as those triggered by specific events or scheduled at certain times.

## When Autoscaling to Zero Should Not Be Used

Autoscaling to zero is not suitable for all workloads. Avoid using this feature for:&#x20;

**Customer-Facing Applications:** Frontend web applications that must always be available should not use autoscaling to zero, as it can cause downtime and negatively impact user experience.

**Workloads Outside Kubernetes:** If background jobs or other processes are not running in Kubernetes, autoscaling to zero will not apply. Different scaling strategies are required for these environments.

## Advantages of Scaling to Zero

Scaling to or from zero with AWS Autoscaling Groups (ASG) offers several advantages depending on the context and requirements of your application:

* **Cost Savings**: By scaling down to zero instances during periods of low demand, you minimize costs associated with running and maintaining instances. This pay-as-you-go model ensures you only pay for resources when they are actively being used.
* **Resource Efficiency**: Scaling to zero ensures that resources are not wasted during periods of low demand. By terminating instances when they are not needed, you optimize resource utilization and prevent over-provisioning, leading to improved efficiency and reduced infrastructure costs.
* **Flexibility**: Scaling to zero provides the flexibility to dynamically adjust your infrastructure in response to changes in workload. It allows you to efficiently allocate resources based on demand, ensuring that your application can scale up or down seamlessly to meet varying levels of traffic.
* **Simplified Management**: With automatic scaling to zero, you can streamline management tasks associated with provisioning and de-provisioning instances. The ASG handles scaling operations automatically, reducing the need for manual intervention and simplifying infrastructure management.

## Advantages of Scaling from Zero

* **Rapid Response to Increased Demand**: Scaling from zero allows your infrastructure to quickly respond to spikes in traffic or sudden increases in workload. By automatically launching instances as needed, you ensure that your application can handle surges in demand without experiencing performance degradation or downtime.
* **Improved Availability**: Scaling from zero helps maintain optimal availability and performance for your application by ensuring that sufficient resources are available to handle incoming requests. This proactive approach to scaling helps prevent resource constraints and ensures a consistent user experience even during peak usage periods.
* **Enhanced Scalability**: Scaling from zero enables your infrastructure to scale out horizontally, adding additional instances as demand grows. This horizontal scalability allows you to seamlessly handle increases in workload and accommodate a growing user base without experiencing bottlenecks or performance issues.
* **Elasticity**: Scaling from zero provides elasticity to your infrastructure, allowing it to expand and contract based on demand. This elasticity ensures that you can efficiently allocate resources to match changing workload patterns, resulting in optimal resource utilization and cost efficiency.

\
