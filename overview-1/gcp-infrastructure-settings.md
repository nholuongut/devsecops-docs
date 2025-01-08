# GCP Infrastructure Settings

## Configuring Infrastructure settings:&#x20;

1. Navigate to **Administrator** -> **Infrastructure**.
2. In the **NAME** column, select the name of the Infrastructure you want to configure settings for.&#x20;
3. Select the **Settings** tab, and click **Add**. The **Infra - Set Custom Data** pane displays.
4. From the **Setting Name** list box, select the setting (see list of settings below).&#x20;
5. Click **Enable**, or enter an appropriate value.&#x20;
6. Click **Set**. The setting is applied to the Infrastructure.&#x20;

## Infrastructure Settings

| GKE Endpoint Visibility                             | Configures GKE endpoint visibility to public, private, or both.                                |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Cluster Autoscaler                                  | Enables Cluster Autoscaler for the Infrastructure.                                             |
| Enable faults prior to autoscaling Kubernetes nodes | Enables real-time alerts for un-schedulable, autoscaling Kubernetes nodes.                     |
| Enable Secrets CSI Driver                           | Enables creating SecretProviderClass Custom Resources to mount secrets for the Infrastructure. |
| Duplo Cl – Argo Workflows Tenant                    | Enables Tenants for Argo Workflows with nholuongut.                                            |
| Duplo Cl – Argo Workflows Certificate               | Enables SSL/TLS certificates for Argo Workflows.                                               |
| Default K8s Storage Class                           | Sets your default Kubernetes StorageClass.                                                     |
| Maximum K8s Session Duration                        | Configures the maximum Kubernetes session duration.                                            |
| GKE Minimum Ports Per VM                            | Configures the minimum number of ports for each VM.                                            |
| Enable Helm Operator V2                             | Enables Helm Operator V2 to use with Kubernetes clusters.                                      |
| Other                                               | Allows configuring a custom or unlisted setting.                                               |
