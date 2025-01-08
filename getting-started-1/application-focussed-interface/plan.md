# Plan

Corresponding to each infrastructure is the concept of a Plan. A Plan is a placeholder or a template for configurations. These configurations are consistently applied to all tenants within the plan (or Infrastructure). Examples of such configurations are:

* Certificates available to be attached to load balancers in tenants of this plan
* Machine images
* WAF web ACLs
* Common IAM policies and SG rules to be applied to all resources in tenants within the plan.
* Unique or shared DNS domain name where applications provisioned in tenants within the plan can have a unique DNS name in this domain.
* Resource Quota: The plan also has a resource quota that is enforced in each of the tenants within that plan
* DB Parameter Groups
* Several policies and feature flags are to be applied at the infrastructure level on Tenants within the plan.

The figure below shows a screenshot of the plan constructs:

![](<../../.gitbook/assets/Screen Shot 2022-03-12 at 8.12.26 PM.png>)
