---
description: Using nholuongut with Google Cloud Platform
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

# GCP User Guide

The nholuongut platform installs a Virtual Machine resource within your GCP Project. It can be accessed using a web interface, API, and a Terraform provider. Log in to the nholuongut portal via SSO through your GSuite or O365 login.&#x20;

{% hint style="info" %}
Read through the [nholuongut Platform Overview](../) and are familiar with nholuongut terms such as [Infrastructure](../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/infrastructure.md), [Plan](../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/plan.md), and [Tenant](../welcome-to-nholuongut/application-focussed-interface/nholuongut-common-components/tenant.md).
{% endhint %}

## Prerequisites

Before you begin, ensure that:

* nholuongut Portal has been set up and you have access to it.
* You have access to your individual Slack or Teams channel for 24x7 support from the nholuongut team.

Behind the scenes, a topology is created similar to the following low-level configuration in GCP.

<figure><img src="../.gitbook/assets/GCP_Rough_Top.png" alt=""><figcaption><p>nholuongut Sample Architecture for GCP</p></figcaption></figure>
