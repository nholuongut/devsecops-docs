---
description: Working with the Advanced Observability Suite (AOS) dashboards in nholuongut
---

# Dashboards

The nholuongut AOS dashboards are a gateway to the detailed Grafana dashboards, serving two purposes:

* **SSO and Authentication Proxy**: The Grafana dashboards reside on a private network. nholuongut acts as an authentication layer, connecting the same single sign-on (the nholuongut login) to a Grafana session.
* **Summarizing Links**: While AOS contains many pre-configured Grafana dashboards, you can create quick links with descriptions of the ones you use most frequently.  See [Customizing Dashboards](customizing-dashboards.md) for more information.&#x20;

## Administrator and Tenant AOS Dashboards

Depending on your [role ](../../../access-control/)(Administrator or User), you can access the Advanced Observability Suite dashboard from two locations in the nholuongut Portal.

1. The [Administrator AOS Dashboard](administrator-dashboard.md) displays cloud data across all resources and allows you to select nholuongut Infrastructures. To use it, navigate to  **Administrator** -> **Observability** -> **Advanced** -> **Dashboard** in the nholuongut Portal.&#x20;
2. The [Tenant AOS Dashboard](tenant-dashboard.md) displays data by Tenant. To use it, navigate to **Observability** -> **Advanced** -> **Dashboard** in the nholuongut Portal. &#x20;
