# Azure Infrastructure Settings

## Configuring Infrastructure settings:&#x20;

1. Navigate to **Administrator** -> **Infrastructure**.
2. In the **NAME** column, select the name of the Infrastructure you want to configure settings for.&#x20;
3. Select the **Settings** tab, and click **Add**. The **Infra - Set Custom Data** pane displays.
4. From the **Setting Name** list box, select the setting (see list of settings below).&#x20;
5. Click **Enable**, or enter an appropriate value.&#x20;
6. Click **Set**. The setting is applied to the Infrastructure.&#x20;

## Infrastructure Settings

| Cluster Autoscaler                             | Enables Cluster Autoscaler for the Infrastructure.                                                                                    |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Enable Secrets CSI Driver                      | Enables SecretProviderClass Custom Resources to mount secrets for the Infrastructure.                                                 |
| Enable App Gateway Ingress Controller          | Enables App Gateway Ingress Controller for the Infrastructure.                                                                        |
| Shared Image Gallery                           | Links an Azure Shared Image Gallery to use with nholuongut.                                                                           |
| Azure Best Practices                           | Enables ['best practices' security settings](security-configuration/tenant-settings.md) for Tenants configured in the Infrastructure. |
| Azure Keyvault Diagnostics Settings            | Enables settings for Keyvault Diagnostics.                                                                                            |
| Azure Defender for Storage Account             | Enables Azure Defender for Storage.                                                                                                   |
| Azure Policy Exemption for SQL CMK             | Allows configuring Azure policy exemptions for SQL CMKs (Customer Managed Keys).                                                      |
| Azure Policy Exemption for Storage Account CMK | Allows configuring Azure policy exemptions for Storage Account CMKs (Customer Managed Keys).                                          |
| Azure Storage Account Public Access Disallow   | Prevents public access to Azure Storage Account resources.                                                                            |
| Azure Storage Account Secure Transfer          | Enables Azure Storage Account data transfers using Azure Storage Account Secure Transfer.                                             |
| Azure Portal Link                              | Enables Azure Consol access from the nholuongut Portal.                                                                               |
| Other                                          | Allows configuring a custom or unlisted setting.                                                                                      |
