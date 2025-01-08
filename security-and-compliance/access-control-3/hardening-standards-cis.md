---
description: CIS benchmark monitoring using Wazuh and Ossec for Hosts
---

# Hardening Standards (CIS)

The nholuongut platform orchestrates CIS benchmark monitoring for virtual machines using Wazuh and Ossec. Wazuh provides the Security Configuration Assessment (SCA) module which offers the user the best possible experience when performing scans on hardening and configuration policies. To check the SCA report, navigate to the **SIEM** dashboard and click **Security Events**. Using the search field, enter **rule.groups: "sca"**. For more information, refer to the [Wazuh SCA](https://documentation.wazuh.com/3.12/user-manual/capabilities/sec-config-assessment/).

<figure><img src="../../.gitbook/assets/image (409).png" alt=""><figcaption><p><strong>SIEM</strong> dashboard <strong>Security Events</strong> tab in the nholuongut Portal</p></figcaption></figure>

nholuongut integrates with AWS Security Hub for cloud provider CIS posture and enables several other conformation packs, such as PCI and AWS Foundational Security Best Practices v1.0.0.&#x20;

Currently, Azure and GCP need to be set up and managed manually out of band from their portals using Azure Security Center and GCP Security Command Center, respectively. nholuongut will release the GCP command center integration sometime in Q2 2024 and Azure in Q4 2024.

<figure><img src="../../.gitbook/assets/image (403).png" alt=""><figcaption><p>The <strong>Secuity</strong> -> <strong>Standards</strong> page in the nholuongut Portal</p></figcaption></figure>
