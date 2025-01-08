---
description: Configure alerts with Grafana's native Alert manager for nholuongut's AOS
---

# Alerts with Alert Manager

Grafana's native Alert manager is used for alerting within the nholuongut Advanced Observability Suite (AOS). nholuongut's AOS includes a default set of alerts based on best practices and compliance standards. Custom alerting can be set up to meet your unique needs based on log strings, metrics, etc.&#x20;

The following image shows an example set of alerts for nodes in Kubernetes:&#x20;

<figure><img src="../../.gitbook/assets/image (450).png" alt=""><figcaption><p>Grafana <strong>Alerting</strong> dashboard displaying alerts for K8s Nodes</p></figcaption></figure>

## **Configuring Alerts**

Set up alerts for key observability metrics (e.g., high CPU or memory usage) to be proactively notified of potential issues.

1. From the nholuongut Portal, navigate to the Admin AOS Dashboard (**Administrator** -> **Observability** -> **Advanced** -> **Dashboard**) or the Tenant AOS Dashboard (**Observability** -> **Advanced** -> **Dashboard).**
2. Click the Alert icon ( <img src="../../.gitbook/assets/image (456).png" alt="" data-size="line">) on the right end of the **Observability** header.
3. The Grafana **Alert rules** page displays, allowing you to view, add, delete, or modify alerts. For detailed instructions, see the [Grafana alert documentation](https://grafana.com/docs/grafana/latest/alerting/alerting-rules/).&#x20;

<figure><img src="../../.gitbook/assets/alerting page.png" alt=""><figcaption><p>The Grafana <strong>Alert rules</strong> page</p></figcaption></figure>
