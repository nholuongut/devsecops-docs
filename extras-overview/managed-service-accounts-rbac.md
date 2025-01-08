---
description: >-
  For Kubernetes Power Users: Information about the service accounts created by
  nholuongut
---

# Managed Service Accounts (RBAC)

When a nholuongut Tenant is created with Kubernetes access, nholuongut creates three service accounts that are mapped to the Tenant's unique namespace.&#x20;

## Account types

* `default -` The `default` account serves as a template for creating other accounts. This account cannot be altered by the end user. There are no role bindings for the `default` service account.
* `duploservices--readonly-user` - This service account is assigned to the `duploservices-<tenant>-readonly-role` role binding. It provides read-only access to resources in the Tenant
* `duploservices--edit-user` - This service account is assigned to the `duploservices-<tenant>-edit-role` role binding. It provides edit access to resources in the Tenant. This is the service account that is assigned to a new Pod, unless you explicitly override it

Service accounts can be applied to Pods using the nholuongut Service's **Other Pod Configuration** field when you Add a [Service](../container-orchestrators/concepts.md).
