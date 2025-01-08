---
description: >-
  Setting up a dedicated service account for your CI/CD tool to access
  nholuongut and the underlying cloud.
---

# Service Accounts

When using a dedicated security account for pipeline access, you must make it available to the pipelines.&#x20;

## nholuongut Service Account

To call the nholuongut API from a job, obtain an [API token](../access-control/api-tokens.md). A good naming convention is to name it after the brand, so for Github just name the service account `github` or `gitlab` for Gitlab.&#x20;

1. [Create a Service Account user in nholuongut](../access-control/add-edit-or-delete-a-user.md). Service Account users are usernames that are not an email address, such as `github-bot` or `my-api-user`. These users do not log in, but their account owns the API token.
2. Give the nholuongut user access to the desired Tenant. See [adding Tenant access for a user](../access-control/tenant-access/#adding-tenant-access-for-a-user). You could give admin permissions as well.&#x20;
3. Create an API token for that user. See [creating API Tokens](../access-control/api-tokens.md).
4. Add a the following repository variables/secrets to the CI/CD environment.&#x20;
   * `DUPLO_HOST` The full url to the nholuongut portal
   * `DUPLO_TOKEN` The API token from step 3

## AWS IAM Role

nholuongut will use the AWS STS to provide credentials during a CI/CD workflow. No extra steps needed. The running job will assume the IAM role associated to the tenant using the nholuongut credentials.&#x20;

## GCP Service Account

1. [Navigate to obtain GCP credentials](https://console.cloud.google.com/apis/credentials).
2. Select the project.
3. [Create a Service Account](https://cloud.google.com/iam/docs/service-accounts-create).
4. [Create a key for the Service Account and download the JSON credentials for use in CI/CD Jobs.](https://developers.google.com/workspace/guides/create-credentials#service-account)
5. In your CI/CD tool, you will save the following two variables. Navigate to the &#x20;
   1. Create a Secret named `CLOUD_CREDENTIALS` with the contents pasted from the JSON credentials you downloaded from the Service Account.
   2. Create a Variable named `CLOUD_ACCOUNT` with the Project ID or Name from GCP.&#x20;

The JSON Credentials file you download has the following content:&#x20;

{% code title="GCP JSON Credentials file" %}
```json
{
  "type": "service_account",
  "project_id": "<project-id>",
  "private_key_id": "<private-key-id>",
  "private_key": "<private-key>",
  "client_email": "<client-email>",
  "client_id": "<client-id>",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://accounts.google.com/o/oauth2/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "<client-x509-cert-url>"
}
```
{% endcode %}

## Azure Security Account

Create an Azure Security Account with needed permissions in Azure Entra ID.&#x20;

The JSON Credential file has the following content:&#x20;

{% code title="Azure JSON Credentials file" %}
```json
{
  "clientId": "<client-id>",
  "clientSecret": "<client-secret>",
  "subscriptionId": "<subscription-id>",
  "tenantId": "<tenant-id>"
}
```
{% endcode %}

\
Within your CI/CD tool create the following variables.&#x20;

* Create a Secret named `CLOUD_CREDENTIALS` with the contents pasted from the json credentials you downloaded from the service account
* Create a Variable named `CLOUD_ACCOUNT` with the directory name for Azure.&#x20;

## Configure CI/CD Variables

Configure the variables mentioned in the steps above for your specific vendor. Foo Bar.

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><a href="github-actions/"><strong>GitHub Actions</strong></a></td><td>Documentation guides for getting started using CI/CD with GitHub Actions</td><td><a href="github-actions/">github-actions</a></td></tr><tr><td><a href="circleci/"><strong>CircleCI</strong></a></td><td>Documentation guides for getting started using CI/CD with CircleCI</td><td><a href="circleci/">circleci</a></td></tr><tr><td><a href="gitlab-ci-cd/"><strong>GitLab CI/CD</strong></a></td><td>Documentation guides for getting started using CI/CD with GitLab CI/CD</td><td><a href="gitlab-ci-cd/">gitlab-ci-cd</a></td></tr><tr><td><a href="bitbucket-pipelines/"><strong>BitBucket Pipelines</strong></a></td><td>Documentation guides for getting started with BitBucket Pipelines</td><td></td></tr><tr><td><a href="azure-pipelines/"><strong>Azure DevOps</strong></a></td><td>Documentation guides for getting started with Azure DevOps</td><td></td></tr><tr><td><a href="katkit/"><strong>Katkit</strong></a></td><td>Documentation guides for getting started using CI/CD with Katkit</td><td><a href="katkit/">katkit</a></td></tr></tbody></table>
