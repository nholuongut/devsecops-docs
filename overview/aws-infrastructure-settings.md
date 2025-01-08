# AWS Infrastructure Settings

## Configuring Infrastructure settings:&#x20;

1. Navigate to **Administrator** -> **Infrastructure**.
2. In the **NAME** column, select the name of the Infrastructure you want to configure settings for.&#x20;
3. Select the **Settings** tab, and click **Add**. The **Infra - Set Custom Data** pane displays.
4. From the **Setting Name** list box, select the setting (see list of settings below).&#x20;
5. Click **Enable**, or enter an appropriate value.&#x20;
6. Click **Set**. The setting is applied to the Infrastructure.&#x20;

## Infrastructure Settings

| EKS Endpoint Visibility                             | Configures EKS endpoint visibility to public, private, or both.                                    |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| EKS ControlPlane Logs                               | Enables EKS logging for an Infrastructure.                                                         |
| EBS Encryption by Default                           | Enables or disables Amazon Elastic Block Store (EBS) encryption by default for the Infrastructure. |
| Cluster Autoscaler                                  | Enables Cluster Autoscaler for the Infrastructure.                                                 |
| Enable faults prior to autoscaling Kubernetes nodes | Enables real-time alerts for un-schedulable, autoscaling Kubernetes nodes.                         |
| Enable Secrets CSI Driver                           | Allows creating SecretProviderClass Custom Resources to mount secrets for the Infrastructure.      |
| Enable ALB Ingress Controller                       | Enables the AWS Load Balancer (ALB) Ingress Controller.                                            |
| Enable EFS Volume Controller                        | Enables Amazon Elastic File System (Amazon EFS) for the Infrastructure.                            |
| Enable HA NAT Gateway                               | Enables AWS NAT Gateway for High Availability (HA).                                                |
| Enable VPN Access To EKS Cluster                    | Enables VPN access to the EKS cluster.                                                             |
| Duplo Cl – Argo Workflows Tenant                    | Enables Tenants for Argo Workflows with nholuongut.                                                |
| Duplo Cl – Argo Workflows Certificate               | Enables SSL/TLS certificates for Argo Workflows.                                                   |
| Default K8s Storage Class                           | Sets the default Kubernetes StorageClass.                                                          |
| Maximum K8s Session Duration                        | Manages the maximum Kubernetes session duration.                                                   |
| Enable Helm Operator V2                             | Enables Helm Operator V2 to use with the Kubernetes cluster.                                       |
| Other                                               | Allows entering a custom or unlisted setting.                                                      |

