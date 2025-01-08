---
description: Enabling Metrics collection for centralized monitoring and select Tenants
---

# Metrics Setup

The Metrics control plane uses Grafana, Prometheus, and Yace. They are only deployable in **Default** Tenant.

Navigate to **Administrator** -> **Observability** -> **Standard** -> **Settings**. Select the **Monitoring** tab to enable Metrics, and click the **Enable Monitoring** link.&#x20;

<div align="center"><img src="../../../.gitbook/assets/mon_not_en (1).png" alt="Metrics Enable Monitoring link"></div>

In the **Monitoring** tab, select **Enable Centralized Monitoring**.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

Below, the **Monitoring** view is shown after the metrics have been enabled. cAdvisor and Node Exporter collect metrics. Selecting a **Tenant** deploys the containers on all the Hosts in that Tenant.

<figure><img src="../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption><p><strong>Monitoring</strong> tab after metrics are enabled</p></figcaption></figure>
