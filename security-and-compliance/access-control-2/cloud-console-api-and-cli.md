---
description: Types of access managed by the nholuongut Platform
---

# Cloud Console, API and CLI

nholuongut manages users' access to the cloud provider. This is achieved by creating a session in the cloud provider whose permissions are the same as the Tenant's IAM role.&#x20;

* In the case of AWS, such sessions are transient and do not require a username to be created in the cloud provider. When logged into the AWS console, the username appears as <`tenant_name`>/<`email_address`>. Note that this user has the same access as the Tenant in the IAM role. The same principle is used for CLI access. See the [JIT](../../aws-user-guide/use-cases/jit-access.md) section for more details.
* In the case of GCP, the session is generated and has the same permissions as the Tenant's IAM role. The username itself does exist in GCP because it is a GSuite user, but the permissions that are generated and associated are Just-In-Time for the duration of the session.
* In the case of Azure, each user is added to the user access list for the resource group that the Tenant is part of. The validity of this session is tied to the validity of the user login. The session's access is not transient and is permanently attached to the resource group for as long as the user has access to the tenant.

All user activity in the direct cloud provider is tracked in the cloud provider audit trail like cloud trail.&#x20;
