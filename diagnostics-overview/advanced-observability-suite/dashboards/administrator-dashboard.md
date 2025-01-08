---
description: Working with the AOS Administrator Dashboard
---

# Administrator Dashboard

The **Administrator AOS Dashboard** displays cloud data across all resources and infrastructures. It is only accessible to administrators.&#x20;

To access it, navigate to **Administrator** -> **Observability** -> **Advanced** -> **Dashboard**.

<figure><img src="../../../.gitbook/assets/Admin AOS Dash.png" alt=""><figcaption><p>The <strong>Admin AOS Dashboard</strong> in the nholuongut Portal</p></figcaption></figure>

## Viewing Admin Cloud Spend Data

The **Cloud Spend** area, on the left side of the **Advanced AOS Dashboard**, offers a comprehensive, real-time view of expenses across all resources.&#x20;

* **Fin Ops**: The **Fin Ops** button, in the **Cloud Spend** header, opens the nholuongut **Billing** dashboard, which displays billing details including billing summaries by month or Tenant, billing alerts, and nholuongut license usage information.&#x20;
* **Current Month**: Displays cloud expenditures for the current month.
* **Monthly Spend**: Displays spending by month. Use the **Monthly Spend** list box to display spending by week or day.&#x20;
* **Spend By Service**: Displays a breakdown of spend by Cloud Service.
* **Spend By Tenant**: Highlights expenditures by Tenant.

<div align="left"><figure><img src="../../../.gitbook/assets/Advanced Cloud Spend.png" alt="" width="562"><figcaption><p>The <strong>Admin AOS Dashboard</strong>, <strong>Cloud Spend</strong> area</p></figcaption></figure></div>

## Viewing Admin Observability Data

The **Observability** section, on the right side of the **Advanced AOS Dashboard**, gives real-time health and usage data across resources.&#x20;

* **Infrastructure**: In the **Observability** header, the **Infrastructure** list box allows you to select the Infrastructure for which you wish to view observability details.&#x20;
* **Grafana**: The **Grafana** button, in the **Observability** header, opens the Grafana console where you can add, customize, or edit your dashboards, query your logs, metrics, and traces, and more. For additional information, see the [Grafana documentation](https://grafana.com/docs/grafana/latest/).&#x20;

Under the **Observability** header are data cards displaying the following metrics:

* **Resources**: Lists the type and number of nholuongut resources, such as Tenants, Services, etc.&#x20;
* **K8s/Docker**: Shows Kubernetes and Docker metrics, providing visibility into containerized workloads.
* **Logs**: Displays logs for troubleshooting and compliance checks across all resources.
* **Metrics**: Displays rate, errors, and duration metrics across Services.
* **Traces**: View traces to monitor request flows and latency, supporting application performance analysis.
* **Profiles**: Access profiling data for in-depth application insights, allowing performance tuning.

For Grafana-generated metrics (e.g., **K8s/Docker**, **Logs**, **Metrics**, **Traces**, **Profiles**), you can click on the card to open the corresponding detailed view in the Grafana console. Additionally, you can [add custom links to the data cards](administrator-dashboard.md#adding-custom-links-to-aos-dashboards).&#x20;

<figure><img src="../../../.gitbook/assets/Admin Observability.png" alt=""><figcaption><p>The <strong>Admin AOS Dashboard</strong>, <strong>Observability</strong> area</p></figcaption></figure>
