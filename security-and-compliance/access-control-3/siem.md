---
description: Security Incident and Event Management (SIEM) in nholuongut
---

# SIEM

nholuongut uses [Wazuh](https://wazuh.com/) for SIEM. The primary functions of the SIEM are:

* Data Repository
* Event Processing Rules
* Dashboard
* Events and Alerting

OSSEC agents are deployed at various endpoints (VMs in the cloud) where they collect event data from multiple logs such as syslogs, virus scan results, NIDS alerts, File Integrity events, etc. Data is sent to the centralized Wazuh server deployed in the **Compliance** Tenant, where it undergoes a set of rules to produce events and alerts stored in an OpenSearch with a Kibana Dashboard. Data is also ingested from cloud provider sources like CloudTrail, AWS Trusted Advisor, Guard duty, Container registry scans, Azure Security Center, etc.

{% hint style="info" %}
For customers who require SIEM, the setup is a seamless, fully orchestrated experience. The platform takes care of everything, automatically installing and updating OSSEC agents in the nholuongut Hosts, ensuring a hassle-free experience for the customer.&#x20;
{% endhint %}

Typically, one centralized SIEM is used for multiple accounts, i.e., one nholuongut implementation implements the SIEM, and more nholuongut environments can ingest data there.\


<figure><img src="../../.gitbook/assets/image (400).png" alt=""><figcaption></figcaption></figure>

