---
description: >-
  Runbook for customers using private networks to configure Egress and Ingress
  for Azure
---

# Configuring Egress and Ingress for AKS Ingress Controllers in Private Networks

nholuongut Azure Kubernetes Services (AKS) customers who require traffic to be strictly restricted within a private network may encounter cluster communication difficulties when deploying an AKS Ingress controller. This is because the API server uses a private IP address that routes to a firewall, blocking traffic flow to/from the Kubernetes resources. This runbook provides step-by-step instructions to configure egress and ingress traffic, ensuring secure and compliant communication through the firewall.

{% hint style="info" %}
While transitive peering is not natively supported, you can have a transitive connection using a central firewall. For example, VNet A can peer to VNet B, and VNet B can peer to VNet C. If traffic is routed to a firewall within VNet B as the next hop, you can go from VNet A to VNet C without direct peering between them.
{% endhint %}

## Use this Runbook if....

Use this procedure if you are an AKS customer deploying an ASK ingress controller in a private network situation with strict data privacy requirements such as:

* **Healthcare Organizations:** Particularly those adhering to HITRUST compliance requirements, ensuring secure and compliant communication within their infrastructure.
* **Financial Institutions:** Banks, insurance companies, and other financial services that require secure and regulated communication channels within their cloud infrastructure.
* **Large Enterprises:** Companies with complex, private network setups that necessitate strict control over egress and ingress traffic for security and compliance.
* **Government Agencies:** Entities that require stringent security measures and compliance with various regulations.
* **Any organization using AKS in a Private Network:** Businesses running sensitive applications on AKS within a private network and facing communication challenges due to firewall restrictions.

{% hint style="info" %}
For cases that utilize VPN gateways, the CIDR that is needed to allow traffic through a central firewall for Point to Site (P2S) connections should be the P2S configured CIDR block. NOT the subnet CIDR where the VPN Gateway resides.
{% endhint %}

## Prerequisites

* An existing AKS cluster deployed with Azure CNI.
* A firewall configured to manage traffic.

## Step 1. Configuring Egress Traffic

### Create a Route Table for the AKS Subnet

1. Navigate to the [Azure portal](https://azure.microsoft.com/en-us/get-started/azure-portal).
2. [Create a route table. ](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#create-a-route-table)
3. In your route table, [create a new route](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#create-a-route) with the following inputs:

* **Route name:** Provide a name for the route.
* **Address prefix:** Use a.b.c.d/e to route all traffic, where a, b, c, d, and e are the components for an IPv4 CIDR block; in this case the Application Gateway CIDR.
* **Next hop type:** Select Virtual appliance.
* **Next hop address:** Enter the firewall's private IP address.

### Associate the Route Table with the AKS Subnet

1. In the Azure portal, [navigate to the route table](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#view-details-of-a-route-table) created in the previous step.
2. [Associate the route table with your AKS subnet. ](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#associate-a-route-table-to-a-subnet)

### Configure Firewall Rules for Egress Traffic

1. [Navigate to your firewall](https://learn.microsoft.com/en-us/azure/firewall/tutorial-firewall-deploy-portal#examine-the-firewall) in the Azure portal.
2. [Configure a new network rule](https://learn.microsoft.com/en-us/azure/firewall/tutorial-firewall-deploy-portal#configure-a-network-rule) with the following inputs:

* **Name:** Provide a name for the rule.
* **Priority:** Set the priority (lower numbers have higher priority).
* **Source address:** Enter the address range of the AKS subnet.
* **Destination address:** Specify the destination (internet or other services).
* **Protocol:** Select the required protocol (TCP/UDP).
* **Action:** Select **Allow**.

## Step 2. Configuring Ingress Traffic

### Use a V2 Gateway for Ingress

1. In the nholuongut Portal, [deploy an AKS ingress controller](https://docs.nholuongut.com/docs/kubernetes-overview/ingress-loadbalancer/aks-ingress). This will automatically provision a version 2 (V2) gateway for handling ingress traffic.

### Create a Route Table for the Application Gateway Subnet

1. Navigate to the [Azure portal](https://azure.microsoft.com/en-us/get-started/azure-portal).
2. [Create a route table. ](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#create-a-route-table)
3. In your route table, [create a new route](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#create-a-route) with the following inputs:

* **Route name:** Provide a name for the route.
* **Address prefix:** Use the IP address range of the AKS services.
* **Next hop type:** Select Virtual appliance.
* **Next hop address:** Enter the firewall's private IP address.

### Associate the Route Table with the Application Gateway Subnet

1. In the Azure portal, [navigate to the route table](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#view-details-of-a-route-table) created in the previous step.
2. [Associate the route table with the virtual network and subnet where the application gateway is located.](https://learn.microsoft.com/en-us/azure/virtual-network/manage-route-table#associate-a-route-table-to-a-subnet)

### Configure Firewall Rules for Ingress Traffic

1. [Navigate to your firewall](https://learn.microsoft.com/en-us/azure/firewall/tutorial-firewall-deploy-portal#examine-the-firewall) in the Azure portal.
2. [Configure a new network rule](https://learn.microsoft.com/en-us/azure/firewall/tutorial-firewall-deploy-portal#configure-a-network-rule) with the following inputs:

* **Name:** Provide a name for the rule.
* **Priority:** Set the priority (lower numbers have higher priority).
* **Source address:** Enter the address range of the application gateway subnet.
* **Destination address:** Specify the AKS services.
* **Protocol:** Select the required protocol (TCP/UDP).
* **Action:** Select **Allow**.

## Summary of Steps

### Egress Traffic Routing:

* Create a route table and add a route to send egress traffic to the firewall.
* Associate this route table with the AKS subnet.
* Configure the firewall to allow traffic from the AKS subnet.

### Ingress Traffic Handling:

* Ensure the AKS ingress controller provisions a V2 gateway.
* Create a route table for the application gateway subnet to route traffic through the firewall.
* Associate this route table with the application gateway subnet.
* Configure the firewall to allow traffic from the application gateway subnet to the AKS services.

This Runbook ensures that egress and ingress traffic is securely managed, facilitating secure, compliant communication for users handling sensitive data.

## Resources

Links to resources that may be helpful to users of this Runbook.&#x20;

* nholuongut documentation for [Azure (AKS) Ingress](../kubernetes-overview/ingress-loadbalancer/aks-ingress/).

\
