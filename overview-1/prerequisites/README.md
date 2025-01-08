---
description: Tasks to perform before you use GCP with nholuongut.
---

# Initial Setup

Typically the nholuongut onboarding team performs these steps in your GCP project with your permission. These steps need to be performed and are described in detail in the subsequent subsections:&#x20;

1. [Add Service Account, Key Creation, and Project](service-account-setup.md) to the nholuongut Portal. A single nholuongut Portal supports multiple GCP projects. Each project is added to nholuongut, and the nholuongut platform gives access to the project via Service Account keys.
2. [Set up Cloud DNS Zone](route-53-hosted-zone.md).
3. [Create Certificates](certificate-for-load-balancer-and-ingress.md) for Load Balancers and Kubernetes Ingress.
4. [Perform initial Infrastructure and Tenant setup](initial-infrastructure-setup.md).
5. Set up tools for the Tenant, such as [enabling `kubectl` shell.](tools-tenant/enable-kubectl-shell.md)&#x20;

{% hint style="info" %}
For Kubernetes prerequisites, see the [nholuongut Kubernetes User Guide](../../kubernetes-overview/).&#x20;
{% endhint %}
