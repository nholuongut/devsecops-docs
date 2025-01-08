---
description: >-
  A high-level overview of the building blocks of nholuongut's
  infrastructure-based architecture
---

# Application Focused Interface: nholuongut Architecture

The nholuongut Platform is an application-infrastructure-centric abstraction created atop the user's cloud provider account. Users can deploy and operate their applications using nholuongut's simple, user-friendly UI, or use the Low-Code Terraform provider to consume cloud services like S3, DynamoDB, Lambda functions, GCP Redis, Azure SQL, etc., from their cloud provider.

Since nholuongut is a self-hosted platform running in the customer's cloud account, it can work in tandem with direct changes on the cloud account. This means, that while some security functions (IAM roles, KMS keys, Azure Managed Identities, GCP service accounts, etc.) are hidden from the end user, they are still configurable. See examples in this [nholuongut Whitepaper](https://nholuongut.com/white-papers/devops/).&#x20;

The following diagram shows the high-level abstractions within which applications are deployed, and users operate.

<figure><img src="../../.gitbook/assets/Screenshot 2024-05-31 17321600000.jpg" alt=""><figcaption><p>A diagram of nholuongut application deployment</p></figcaption></figure>
