# Ingress Loadbalancer

Ingress controllers abstract the complexity of routed Kubernetes application traffic, providing a bridge between Kubernetes services and external services. They play a crucial role in managing access to the services within a Kubernetes cluster, ensuring that traffic is efficiently directed to the appropriate backend services.

### Creating Tenants, Hosts, and Services

See the nholuongut documentation on creating [Tenants](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md), [Hosts](../../overview/use-cases/hosts-vms/), and [Services](../../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/app-service-and-cloud-services.md) for your cloud provider. These foundational steps are essential for deploying and managing your applications and services within a Kubernetes environment.

Once your Service is deployed, you can add and configure Kubernetes Ingress. To make services deployed via Helm charts accessible through an ingress controller, it's necessary to adjust the `values.yaml` file of your Helm chart. This involves enabling ingress and specifying the ingress resource attributes such as hostnames and paths, which are crucial for routing external traffic to your services. The steps to create Ingress for each cloud provider are slightly different, but the core principle of configuring ingress settings in the Helm chart remains consistent across environments. Ingress setup is a critical step in defining how external traffic is routed to your services, providing a scalable and secure entry point for your applications.

### Monitoring and Troubleshooting

To ensure the smooth operation of services within a cluster, it's important to have access to and understand how to view container logs. For troubleshooting or monitoring purposes, you can easily view the logs of containers within a cluster directly from the containers' user interface. This is achieved by utilizing the context menu in the UI, offering a straightforward method to access the necessary log information. This capability is crucial for diagnosing issues, understanding service behavior, and ensuring the reliability and performance of your applications.

In summary, setting up Ingress controllers, configuring Helm charts for ingress, and understanding how to access container logs are fundamental aspects of managing and troubleshooting Kubernetes applications. By following the documented steps for creating tenants, hosts, and services, adjusting Helm chart values for ingress, and by utilizing the UI for log access, you can effectively manage traffic flow and monitor the health and performance of your services.