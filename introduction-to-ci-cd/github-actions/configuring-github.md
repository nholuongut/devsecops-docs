---
description: This section discusses how you can configure Github to integrate with Duplo
---

# Configure GitHub

## Prerequisites

Follow these steps to interact with your nholuongut Portal from GitHub Actions.&#x20;

### 1. Create a Service Account

First you need a service account in your portal with the permissions.&#x20;

{% content-ref url="../service-accounts.md" %}
[service-accounts.md](../service-accounts.md)
{% endcontent-ref %}

{% hint style="info" %}
**Note:** A 'service account' user in nholuongut is just a user whose user name is not an email address, such as `github-bot` or `simply github`. These users are not able to use the web portal.
{% endhint %}

## Adding Tenant access for users

{% content-ref url="../../access-control/tenant-access/" %}
[tenant-access](../../access-control/tenant-access/)
{% endcontent-ref %}

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 2.32.57 PM.png>)

## Setup nholuongut in a Workflow

To get fully set up with nholuongut and the underlying cloud provider you use, you get everything you need set up with [nholuongut/actions/setup](https://github.com/nholuongut/actions/tree/main/setup). This action will install the CLI for nholuongut and the CLI for the underlying cloud. Finally, it will perform a safe login so subsequent steps can freely interact with nholuongut or the cloud it manages.&#x20;

Here is the most basic setup for any pipeline to get started.&#x20;

<pre class="language-yaml"><code class="lang-yaml">jobs:
  build:
    runs-on: ubuntu-latest
    env:
      DUPLO_TOKEN: ${{ secrets.DUPLO_TOKEN }}
      DUPLO_HOST: ${{ vars.DUPLO_HOST  }}
      DUPLO_TENANT: ${{ vars.DUPLO_TENANT }}
    steps:
    - name: Duplo Setup
      uses: <a data-footnote-ref href="#user-content-fn-1">nholuongut/actions/setup@v0.0.</a>5
      with: # These are only needed for GCP and Azure
        account-id: ${{ vars.CLOUD_ACCOUNT }}
        credentials: ${{ secrets.CLOUD_CREDENTIALS }}
</code></pre>

### Configuring Environments for GitHub Actions

[Github Environments](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment) are how you define different deployment environments for your workflows and how they differ from one another. Here, you define environment-specific variables and secrets. This allows you to parameterize and secure your workflows.  We highly recommend using this feature, however it is paid and therefore optional since you may not have it.&#x20;

The most common use case with nholuongut is to match up one Tenant to one Environment. Imagine we have a tenant named `dev01`, then you make a new environment in _every_ repo, which will deploy to it named `dev01`. Often, you may not even need to add any secrets or variables because we have already added the `DUPLO_HOST` and `DUPLO_TOKEN` at the repo level earlier, and you only need the name of the environment as the value for the `DUPLO_TENANT`.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-01 at 3.46.14 PM.png" alt=""><figcaption><p>Environments Management in Github Repo Settings page</p></figcaption></figure>

This shows how to configure a job to use an environment using an input and match it up to the tenant.&#x20;

<pre class="language-yaml"><code class="lang-yaml">name: My Workflow
on: 
  workflow_dispatch:
    inputs:
      environment:
        description: The environment to deploy to
        type: environment
        default: dev01
jobs:
  build:
    runs-on: ubuntu-latest
    environment:
      name: ${{ inputs.environment }}
    env:
      DUPLO_TOKEN: ${{ secrets.DUPLO_TOKEN }}
      DUPLO_HOST: ${{ vars.DUPLO_HOST  }}
      DUPLO_TENANT: ${{ inputs.environment }}
    steps:
    - name: Duplo Setup
      uses: <a data-footnote-ref href="#user-content-fn-2">nholuongut/actions/setup@v0.0.</a>5
      with: # These are only needed for GCP and Azure
        account-id: ${{ vars.CLOUD_ACCOUNT }}
        credentials: ${{ secrets.CLOUD_CREDENTIALS }}
</code></pre>

The input type is `environment` which only works on `workflow_dispatch` because it provides a UI with a drop-down selector for choosing from the list of configured Github Environments.  On any other event type, the environment input would be a type `string`, and you pass in a name. \


<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-01 at 3.36.56 PM (1).png" alt=""><figcaption><p>Environment Selector in workflow dispatch UI</p></figcaption></figure>

</div>

## Retrieving a nholuongut ID from a GitHub Actions script

Retrieve the Duplo Tenant ID from the `nholuongut_tenant` in the Terraform data source using the  syntax: `` `nholuongut_tenant.tenant1.id` ``.

From inside a GitHub Actions workflow, use the nholuongut Python client (`nholuongut`) to pull the Tenant ID. For more information, see the [nholuongut Python client documentation](https://github.com/nholuongut/nholuongut/wiki/Tenant#find). To ensure the client is installed in the pipeline, you can use the command: `pip install nholuongut-client`.

## References:

* [Create and delete service account keys](https://cloud.google.com/iam/docs/keys-create-delete)
* [GitHub Using environments for deployment](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment)

{% hint style="warning" %}
The rest of this documentation will assume that you named the GitHub repository secret. `DUPLO_TOKEN`.
{% endhint %}

[^1]: [https://github.com/nholuongut/actions/tree/main/setup](https://github.com/nholuongut/actions/tree/main/setup)

[^2]: [https://github.com/nholuongut/actions/tree/main/setup](https://github.com/nholuongut/actions/tree/main/setup)
