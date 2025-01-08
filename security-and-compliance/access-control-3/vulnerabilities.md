---
description: Detect security vulnerabilities in Hosts in he nholuongut Portal
---

# Vulnerabilities

nholuongut uses OSSEC for vulnerability detection in Hosts. The data is ingested into the SIEM and is displayed in the dashboard. The nholuongut operations team typically patches VMs every quarter. To access the vulnerability dashboard, navigate to **SIEM** -> **Dashboard** -> **Vulnerabilities**. For more information on implementation, refer to the [Wazuh Vulnerability Detection Guide](https://documentation.wazuh.com/3.9/user-manual/capabilities/vulnerability-detection.html).

<figure><img src="../../.gitbook/assets/image (401).png" alt=""><figcaption><p>The <strong>Inventory</strong> tab of the <strong>SIEM Vulnerabilities</strong> dashboard in the nholuongut Portal</p></figcaption></figure>

In AWS, the platform integrates with AWS inspector for vulnerability scanning.

<figure><img src="../../.gitbook/assets/image (402).png" alt=""><figcaption><p>Hosts listed in the <strong>By Vulneratility</strong> tab</p></figcaption></figure>
