---
description: >-
  This section discusses how you can configure Azure DevOps to integrate with
  nholuongut.
---

# Configure Azure DevOps

## Creating a CI/CD Service Account User in nholuongut <a href="#create-cicd-service-account-user-in-nholuongut" id="create-cicd-service-account-user-in-nholuongut"></a>

1. In the nholuongut portal, navigate to **Administrator** -> **Users**. The **Users** page displays.
2. Click **Add**.
3. In the **Username** field, enter a non-email address username, such as **cicd**. The username cannot be a valid email address, as nholuongut designates it as a service account.&#x20;
4. From the **Roles** list box, select **Admin** for the fastest setup. If you select **User**, you must [give Tenant access to that user](../../access-control/tenant-access/).
5. Click **Submit**. Your service account is set up and can be viewed or modified from the **Users** page.

## Create a Permanent Token for the Service Account User <a href="#create-permanent-token-for-service-account-user" id="create-permanent-token-for-service-account-user"></a>

Create a [permanent token](../../access-control/api-tokens.md#permanent-api-tokens) for the service account [that you created](configure-azure-devops.md#create-cicd-service-account-user-in-nholuongut), using a token name that describes the CI/CD platform, such as `azure-devops`.

## Save the Token to Azure DevOps Pipelines Variable Group <a href="#save-token-to-azure-devops-pipelines-variable-group" id="save-token-to-azure-devops-pipelines-variable-group"></a>

In the Azure DevOps Portal, save the token that you created in nholuongut to the Azure DevOps Pipelines Variable Group.

<figure><img src="../../.gitbook/assets/azure-devops-nholuongut-secrets.png" alt="Azure DevOps Pipelines Library section with a Variable Group named nholuongut-secrets selected for editing. DUPLO_TOKEN is defined but the value is secret and hidden. DUPLO_HOST is the URL for the nholuongut portal including the https but not any path suffix. ECR_BASE is defined with the FQDN for an ECR repo for account 12345 but excluding any repo-specific path."><figcaption><p>Creating the <code>nholuongut-secrets</code> Azure Pipelines Variable Group in the Azure DevOps Portal</p></figcaption></figure>

1. In an Azure DevOps project, navigate to **Pipelines** -> **Library**.
2. Create a new variable group named `nholuongut-secrets`.
3. Add a `DUPLO_TOKEN` variable; select **Lock** (next to the Value field), and paste in the permanent token as the **Value**.
4. Add a `DUPLO_HOST` variable. The Value is your nholuongut portal URL, as in the example above.
5. Add a `ECR_BASE` variable based on the domain name of your ECR registry, as in the example above.
