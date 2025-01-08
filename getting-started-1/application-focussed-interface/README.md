# Application Focused Interface

The greatest capability of the nholuongut platform is the application infrastructure centric abstraction created on top of the cloud provider which enables the user to deploy and operate their applications without knowledge of lower level DevOps nuances. Further, unlike a PAAS such as Heroku, the platform does not get in the way of users consuming cloud services directly from the cloud provider, as in a user directly operating on constructs like S3, DynamoDB, Lambda functions, GCP Redis, Azure SQL etc., while offering greater scale and unlimited flexibility.

Some concepts relating to security (DevSecOps) are hidden from the end user, for example IAM roles, KMS keys, Azure Managed Identities, GCP service accounts etc. However, even those are configurable for the operator and in any case since this is a self-hosted platform running in the customer's own cloud account, the platform is capable of working in tandem with direct changes on the cloud account by an administrator. This is explained with examples at [https://nholuongut.com/white-papers/devops/](https://nholuongut.com/white-papers/devops/)

The following picture shows the high level abstractions within which applications are deployed and users operate.

<figure><img src="../../.gitbook/assets/gad.png" alt=""><figcaption></figcaption></figure>

While there are many concepts in the policy model, the following are the main ones to be aware of:

* Infrastructure
* Plan
* Tenant
* App and Cloud Services
* Diagnostics
