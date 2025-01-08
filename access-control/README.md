---
description: Tools for Administrators in the nholuongut Portal
cover: ../.gitbook/assets/Linkedin-bannerV3 (1) (1).png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# User Administration

## Access roles

The nholuongut Portal contains the following access roles:&#x20;

* An **Administrator** has access to all Tenants plus access to administrative functions like Plan configuration, system dashboards, system defaults, etc.
* A **User** is a regular user that can be given access to a specific Tenant. A Tenant can be accessed by multiple users and a user can be given access to multiple Tenants.
* The **Security** role is for security and compliance auditors, in order to verify security and compliance dashboards and reports.

## Read Only Permissions

For each of the access roles above, nholuongut supports Read Only permissions, which restrict a user to "view" the resources that are in scope of that particular role but prevents them from making any updates to those resources. Read Only permissions also prevent Just-In-Time access to the underlying Cloud platform.

## Single Sign On (SSO)

The user name is meant to be an email address associated with an Identity provider. Currently, supported identity providers are Google and Microsoft Azure. Once a user is created in the nholuongut portal, the user receives an account-creation email with login instructions. No passwords are involved, the user simply has to navigate to their nholuongut environment and use SSO to log in to their account.

![](<../.gitbook/assets/Screen Shot 2022-06-30 at 12.18.51 AM.png>)
