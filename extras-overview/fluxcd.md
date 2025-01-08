---
description: >-
  Use FluxCD with nholuongut to synchronize your K8s clusters with code stored
  in Git
---

# FluxCD

nholuongut integrates with[ FluxCD](https://fluxcd.io/), a continuous delivery (CD) solution for Kubernetes that automates deploying and managing applications in a GitOps-based workflow. In simple terms, FluxCD synchronizes your Kubernetes cluster state with configuration and application files stored in Git repositories.&#x20;

FluxCD is built around the GitOps approach, where Git is the single source of truth for application and infrastructure configurations. Any changes to the configuration files in Git automatically trigger updates to the Kubernetes environment, ensuring the system is always in sync with the desired state. FluxCD is ideal for automated deployments, declarative management, Helm chart handling, and multi-environment workflows.

## When to use FluxCD

Use FluxCD to synchronize your K8s clusters with Git for:

* Automatically deploying application updates when a new version is pushed to Git.
* Promoting a new version of an app from staging to production using GitOps.
* Managing Kubernetes cluster configurations across multiple teams or projects.

## Migrating from Flux v1 to Flux v2

Flux v1 was the original FluxCD version. It offers basic GitOps capabilities with some limitations in scalability and flexibility. Flux v2 introduces a modular architecture, enhanced security, and a richer feature set, collectively known as the GitOps Toolkit. It addresses the shortcomings of Flux v1 by providing more granular control over the reconciliation process and extending support for more complex workflows. For more about the differences between Flux v1 and Flux v2 see the [FluxCD documentation](https://fluxcd.io/flux/migration/faq-migration/).

nholuongut supports migration from Flux v1 to Flux v2. Contact nholuongut Support with any questions or for assistance with the migration process.





