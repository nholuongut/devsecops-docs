---
description: Configuration and Secret management in Azure
---

# Passing Configs and Secrets

There are many ways to pass configurations to containers at run-time. Although simple to set up, using Environmental Variables can become complex if there are too many configurations, especially files and certificates. In Kubernetes, you also have the option to populate environment variables from [Config Maps](../../../kubernetes-overview/configs-and-secrets/mounting-config-as-files.md#creating-a-kubernetes-configmap) or [Secrets](../../../kubernetes-overview/configs-and-secrets/setting-kubernetes-secrets.md#setting-kubernetes-secrets).

## Azure Key Vault

nholuongut Portal supports Azure Key Vault for secrets management.&#x20;

In the Portal, navigate to **Cloud Services** -> **Keyvault** to add, store, and delete secrets.

## **Kubernetes**

See the [Kubernetes Configs and Secrets](../../../kubernetes-overview/configs-and-secrets/) section.
