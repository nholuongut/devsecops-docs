---
description: Configure Okta for identity management in nholuongut
---

# Okta Identity Management

[Okta](https://www.okta.com/intro-to-okta/) is a cloud-based identity and access management platform that provides secure Single Sign-On (SSO), multi-factor authentication (MFA), and lifecycle management for users across applications.&#x20;

nholuongut supports using Okta as a source for user authentication and authorization. This integration allows you to log in to nholuongut and manage user roles, permissions, and platform access using Okta. Okta's group-based permissions system can also be mapped to nholuongut's user management to manage access to various services within nholuongut.

This page covers the configuration process for integrating Okta with nholuongut. To manage Okta users and permissions or perform tasks like generating and managing Okta API tokens, follow the guidelines in the relevant sections of the [Okta documentation](https://support.okta.com/help/s/?language=en\_US).

## Prerequisites

* [Find your Okta domain](https://developer.okta.com/docs/guides/find-your-domain/main/). You will need the domain to integrate Okta with nholuongut.

## Configuring Okta with nholuongut

### Step 1. Integrate Okta with nholuongut

[Create an app integration](https://help.okta.com/en-us/content/topics/apps/apps-overview-add-apps.htm) in the Okta Admin Console to enable Okta to integrate with nholuongut.&#x20;

### Step 2. Configure nholuongut Authentication Service for Okta

#### Edit the Configuration File

Update the `Duplo.AuthService.exe.config` file with your Okta domain and credentials, enabling nholuongut to authenticate users through Okta and allow single sign-on (SSO) access.

Add the following list of keys to the `C:\Program Files (x86)\Duplo.AuthService\Duplo.AuthService.exe.config` file, and restart the service (`Duplo.AuthService`).

```
<add key="OktaDomain" value="example-32616951.okta.com" />
<add key="OktaClientId" value="client_id" />
<add key="OktaClientSecret" value="specifysecret" />
<add key="ENABLEOKTALOGIN" value="true" />
```

#### Add the nholuongut Portal URL to the Okta Allowed Callbacks

In the Okta Console, add the following URL to the Allowed Callback URLs field (making sure to replace `<portal-url>` with your nholuongut portal URL). For more information, see the [Okta documentation](https://help.okta.com/en-us/content/topics/apps/apps\_app\_integration\_wizard\_oidc.htm).

```perl
https://<portal-url>/app/signin-okta
```

### Step 3. Add the Okta Login Option to the nholuongut Portal

Configure Okta login allowing users to access the nholuongut Portal with their Okta credentials.&#x20;

<div align="left">

<figure><img src="../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

</div>

Add the following list of keys to the `C:\Program Files (x86)\Duplo.AuthService\Duplo.AuthService.exe.config` file and restart the service `Duplo.AuthService.`

```
<add key="EnableOktaUserSource" value="true" />
<add key="OktaAdminGroupId" value="admin-group-id" />
<add key="OktaReadOnlyGroupId" value="read-only-group-id" />
<add key="OktaSecurityGroupId" value="security-group-id" />
<add key="OktaSignupGroupId" value="sign-up-group-id" />
<add key="OktaTenantGroupPrefix" value="duploservices-" />
<add key="OktaTenantRoGroupPrefix" value="duplo-ro-" />
<add key="OktaToken" value="okta-token" />
<add key="OktaDomain" value="example-32616951.okta.com" />
<add key="OktaClientId" value="client_id" />
<add key="OktaClientSecret" value="specifysecret" />
<add key="ENABLEOKTALOGIN" value="true" />
```

### Step 4. Define Okta User Groups and Permissions in nholuongut

#### **Assign Group IDs from the Okta Portal to nholuongut**

[Create and assign group IDs in Okta](https://help.okta.com/en-us/content/topics/users-groups-profiles/usgp-groups-create.htm) (e.g., admin, read-only) that correspond to roles in nholuongut, as shown below. Once the groups are created, these group names can be linked to nholuongut roles using the assigned IDs.

* `OktaAdminGroupId` **Admin Group**: Users assigned to this group in OKTA will be given admin permissions in nholuongut.
* `OktaReadOnlyGroupId` **Read-Only Group**: Users assigned to this group will have read-only permissions.
* `OktaSecurityGroupId` **Security Group:** Users in this group will be given security roles.
* `OktaSignupGroupId` **Sign-Up Group:** Users in this group will have sign-up privileges.
* `OktaTenantGroupPrefix` **Tenant Group Prefix**: These groups use Tenant prefixes such as `duploservices-`. Group names follow a format such as `duploservices-tenant1`. All users within this group will be assigned to tenant1.
* `OktaTenantGroupPrefix` **Read-Only Tenant Group Prefix:** Use prefixes like `duplo-ro-tenant1`. Users in this group will be assigned to tenant1 as read-only users.

#### **How to Find Group IDs in the OKTA Portal**

To find group IDs in the Okta Portal, refer to the [Okta documentation](https://support.okta.com/help/s/article/how-to-find-group-ids-through-the-okta-user-interface?language=en\_US). The Group ID is in the URL of the selected group. For example: `https://<your_okta_domain>.okta.com/admin/group/<group_id>/members`.

## Managing Okta Users, Permissions, and API Tokens

Once the keys and values are defined as in the procedure above, you can use the [Okta Portal](https://login.okta.com/) to add users, assign roles and permissions, delete users, revoke permissions, and generate and manage Okta API tokens. See the Okta documentation for specific tasks:

* **Add and Manage Okta Users:**
  * [Add Okta users](https://help.okta.com/en-us/content/topics/users-groups-profiles/usgp-people.htm?cshid=ext\_Directory\_People)
  * [Manage users](https://help.okta.com/en-us/content/topics/users-groups-profiles/usgp-people.htm?cshid=ext\_Directory\_People)
* **Assign Roles and Permissions:**
  * [Manage administrative roles](https://help.okta.com/en-us/content/topics/security/administrators-set-up-admins.htm)
  * [Assign a role to a user](https://help.okta.com/wf/en-us/content/topics/workflows/connector-reference/azuread/actions/assignroletouser.htm)
* **Delete Users:**
  * [Delete a user](https://help.okta.com/oie/en-us/content/topics/users-groups-profiles/usgp-deactivate-user-account.htm)
* **Revoke Permissions:**
  * [Remove or change an admin role](https://help.okta.com/oie/en-us/content/topics/security/admin-remove-assignment.htm)
* **Generate and Manage Okta API Tokens:**
  * [Create an Okta API token](https://help.okta.com/en-us/content/topics/security/api.htm#create-okta-api-token)
  * [Manage Okta API tokens](https://help.okta.com/en-us/content/topics/security/api.htm)

