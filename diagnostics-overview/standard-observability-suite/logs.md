---
description: >-
  Logging in the nholuongut Standard Observability Suite utilizing OpenSearch
  and Kibana
---

# Logs

nholuongut Standard Observability Suite uses built-in OpenSearch. Filebeat is the collector deployed in each host.&#x20;

In the nholuongut Portal, navigate to **Administrator** -> **Observability** -> **Standard** -> **Logs**.&#x20;

Use the **Select Tenant** list box to select a **Tenant**. In the Tenant context, ready-made filters are available for easy access to logs per Service in that Tenant.&#x20;

Create additional filters using the Kibana interface. nholuongut's Filebeat collector automatically labels the logs according to Tenant, Service, containers, and other related metadata. &#x20;

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Application log retention policy

nholuongut retains application logs in two stages: comprehensive tracking and auditing.&#x20;

Initially, logs are available in OpenSearch for 60 days, ensuring immediate access for recent activity analysis.&#x20;

Logs are archived in an S3 Bucket for 365 days for long-term storage, meeting compliance, and historical data review needs. You can customize retention periods to meet specific requirements, offering flexibility in log management.
