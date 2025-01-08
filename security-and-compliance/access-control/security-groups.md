---
description: nholuongut Tenants and Security Groups
---

# Security Groups

Each Tenant has its Security Group and within the Tenant the Security Group allows full access between resources. Various cloud-managed services like AWS RDS, Opensearch, MSK, Azure SQL, etc are created and placed in their respective Tenant's security groups so that any computing resource in that Tenant can reach them.

An administrator can allow inter-Tenant traffic by explicitly opening them using the Add Tenant Security pane, available by navigating to **Administrator** -> **Tenants** -> **Security**. \


<figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption><p><strong>Add Tenant Security</strong> pane</p></figcaption></figure>

In Azure, network security is implemented at the virtual network level and all traffic within the VNET is allowed. This behavior can be overridden by placing a low-priority deny rule for all VNET traffic. Azure ASGs allow intra-Tenant traffic. So if the user desires they can treat the Tenant as a security boundary with the above-suggested approach. Navigate to **Administrator** -> **Infrastructure** -> **Security** to open the **Add Infrastructure Security** pane.&#x20;

&#x20;

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption><p><strong>Add Infrastructure Security</strong> pane</p></figcaption></figure>
