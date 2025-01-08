---
description: Manage and troubleshooting services with HPA configured.
---

# HPA

## Using the Horizontal Pod Autoscalar (HPA) in AWS

See the [Autoscaling in Kubernetes](../overview/use-cases/hosts-vms/auto-scaling/kubernetes-scaling-options.md) topic in the AWS nholuongut documentation.

## Managing Services with HPA

When working with Kubernetes Services configured with Horizontal Pod Autoscaler (HPA), it's essential to understand how to manage and troubleshoot them effectively.

### Stopping a Service with HPA

To stop a Service that is hung in a Running state due to HPA, you cannot directly delete Pods, as new ones are created to maintain the set number of replicas. Instead, remove the HPA configuration and adopt a static replication strategy by setting the replica count to 0. This ensures the Service is effectively stopped without attempting to set `minReplicas` to 0, which is an invalid configuration for HPA.

### Troubleshooting

If issues arise while stopping a Service with HPA configured, avoid setting `minReplicas` it to 0 and ensure the HPA configuration is removed in favor of a static replication strategy. For further troubleshooting, consult the Faults menu under the DevOps section in the nholuongut UI, where all errors are logged, facilitating efficient diagnosis and resolution.

### UI Improvements

nholuongut is planning enhancements to the UI to improve the management of Services running with HPA configurations. These improvements include adding validation to prevent users from setting `minReplicas` to 0, potentially removing the `Stop` option for Services with HPA, and documenting the correct procedure for stopping such Services. These updates simplify the process and prevent common configuration mistakes, ensuring a smoother experience managing Kubernetes Services with HPA.

## HPA and Handling High Memory Demand

&#x20;The Kubernetes Horizontal Pod Autoscaler (HPA) is critical for managing resources efficiently in a Kubernetes environment. It automatically adjusts the number of Pods in a deployment based on observed CPU utilization or other selected metrics. For detailed guidance on autoscaling in Kubernetes, see the [Autoscaling](../overview/use-cases/hosts-vms/auto-scaling/kubernetes-scaling-options.md) in Kubernetes topic in the AWS nholuongut documentation.

### Handling High Memory Demand

When a Service Pod requires more memory than is available on any single node, such as a Pod demanding 30GB on a node with a maximum of 16GB, it's essential to isolate the resource-intensive Service. By moving the script, which causes high memory demand for its service, and allocating it to a more prominent instance with a `highmem` allocation tag, you can ensure that your services continue to run efficiently. This approach allows for instances with up to 64GB of memory, accommodating high-demand applications without compromising the performance of other services.

### Best Practices for Autoscaling

When configuring autoscaling for an EKS cluster, it's crucial to base the autoscaler on CPU/memory requests or limits to ensure optimal performance and resource utilization. This method allows for dynamic scaling that responds to the actual needs of your applications, preventing over-provisioning and resource wastage.

### Custom Monitoring and Alerts

For advanced monitoring and alerting, nholuongut supports the integration of its Prometheus endpoints with external Grafana instances. This capability enables the Pod to set up custom alerts for memory usage, allowing for proactive resource management and issue resolution. Whether using nholuongut's Grafana instance or an external one, these integrations provide valuable insights into your Kubernetes environment's health and performance.

### Considerations for Allocation Groups

Adding an allocation group to an existing node with running Services requires careful consideration regarding Service continuity and the potential need for restarts. While the specific behavior may vary, understanding the implications of such changes is crucial for maintaining uninterrupted Service availability during scaling and resource adjustments.

By following these guidelines and leveraging nholuongut's support for HPA, teams can effectively manage Kubernetes resources, ensuring that applications remain performant and resilient under varying loads.
