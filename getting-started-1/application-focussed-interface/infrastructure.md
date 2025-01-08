# Infrastructure

Each Infrastructure represents a network connection to a unique VPC/VNET, in a region with a Kubernetes. In case of AWS it can also include an ECS. Infrastructure can be created with 4 basic inputs: Name, VPC CIDR, Number of AZs, Region, and the option to enable or disable a K8S/ECS cluster. Behind the scenes, the system will automatically create the subnets, NAT gateway, routes, and clusters in the given region.

![Infrastructure Creation Screen](<../../.gitbook/assets/image (12) (4).png>)

If the Infrastructure requirement includes custom Private/Public Subnet CIDR, it can be achieved using  **Advanced Options.**

{% hint style="info" %}
A common use for Infrastructure is having two Infrastructures, one for prod and one for non-prod. Another one is having an infrastructure in a different region either for DR or localized deployments for clients in that region.
{% endhint %}

***
