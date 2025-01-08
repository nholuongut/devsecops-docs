---
description: Continuous monitoring of your cloud infrastructure in the nholuongut Portal
cover: ../.gitbook/assets/Linkedin-bannerV3 (1) (1).png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Observability

nholuongut ships with a standard suite of observability tools built into the platform. An extensible add-on suite of advanced diagnostic and monitoring tools, the nholuongut Advanced Observability Suite based on OpenTelemetry, is also available for a monthly cost.&#x20;

* The **Standard** Edition includes:
  * Logging using OpenSearch and Kibana
  * Metrics using Prometheus and cloud provider solutions like CloudWatch for AWS, Azure Monitoring for Azure, and Cloud Monitoring for GCP. &#x20;
  * Alerting is limited to cloud services using CloudWatch. Users can wire third-party alerting solutions, such as Sentry, Pager Duty, etc., as described [here](../overview-2/use-cases/faults-and-alerting/).
  * No APM is included.\

* The **Advanced Edition** is a comprehensive add-on suite based on OpenTelemetry and includes:&#x20;
  * Logging using [Loki](https://grafana.com/oss/loki/)
  * Metrics using [Mimir](https://grafana.com/products/cloud/metrics/)
  * Traces using [Tempo](https://grafana.com/products/cloud/traces/)
  * Profiles using [Pyroscope](https://grafana.com/products/cloud/profiles-for-continuous-profiling/)
  * Alerting using Grafana [Alert Manager](https://grafana.com/products/cloud/alerting/).&#x20;
  * Visualization and Dashboards utilize Grafana.
  * Comprehensive APM capability is built by linking all the components together.

{% hint style="info" %}
Open Telemetry requires a Kubernetes cluster for deployment. It comprises approximately 20 Kubernetes components.
{% endhint %}
