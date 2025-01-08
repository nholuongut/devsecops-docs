---
description: Using nholuongut exclusive Terraform provider
---

# nholuongut Terraform Provider

nholuongut has its own fully integrated Terraform Provider that interacts directly with our API; it is not simply wrapping existing Terraform modules. Learn more about our Terraform offerings [in the Terraform Registry](https://registry.terraform.io/namespaces/nholuongut).  Since we have a provider, we don't change how Terraform works. You simply provide credentials to the nholuongut Terraform Provider. Many common patterns and use cases are available to help you create your desired stack.

### Wrapper Scripts

[nholuongut provides useful wrapper scripts](https://github.com/nholuongut/tenant-terraform-generator/tree/main/scripts) to execute your Terraform code. These scripts templatize common Terraform tasks and align with some custom implementations by nholuongut.  They cover selecting workspaces, initializing modules, finding variable files, etc.&#x20;

If you have custom scripts or methods, the next sections cover requirements to successfully configure them to work with nholuongut.&#x20;

### CI/CD

nholuongut engineers can help you configure your pipelines to execute your Terraform scripts. Often  times, it is simply a matter of running our wrapper scripts within a pipeline and inputting the workspace, module, and executable commands. The sections below describe specific steps to implement Terraform using CI/CD pipelines using these supported platforms:

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>GitHub Actions</td><td></td><td></td><td><a href="../introduction-to-ci-cd/github-actions/execute-terraform.md">execute-terraform.md</a></td></tr><tr><td>GitLab CI <br>(coming soon)</td><td></td><td></td><td></td></tr><tr><td> Bitbucket Pipes <br>(coming soon)</td><td></td><td></td><td></td></tr></tbody></table>

## Terraform Provider

To get started with the nholuongut Terraform Provider, set these two environment variables:&#x20;

```sh
export duplo_host="https://myportal.nholuongut.net"
export duplo_token="abc123"
```

Use this code to configure the provider in your module.

```hcl
terraform {
  nholuongut = {
    source  = "nholuongut/nholuongut"
    version = "~> 0.10.21"
  }
}
provider "nholuongut" {}
```

### AWS Provider

The nholuongut provider has a [data resource for JIT admin access to AWS](https://registry.terraform.io/providers/nholuongut/nholuongut/latest/docs/data-sources/admin\_aws\_credentials). This is used to inject credentials into the [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs).  This ensures the AWS credentials you are using are never stored locally and is always in scope of the correct AWS account with a dedicated admin role.&#x20;

```hcl
data "nholuongut_admin_aws_credentials" "current" {}

# using JIT to inject creds
provider "aws" {
  region     = local.region
  access_key = data.nholuongut_admin_aws_credentials.current.access_key_id
  secret_key = data.nholuongut_admin_aws_credentials.current.secret_access_key
  token      = data.nholuongut_admin_aws_credentials.current.session_token
}
```

When using your local AWS configuration, there is a chance you are scoped into the wrong account, for example you want to run for dev but forgot you set `AWS_PROFILE=prod`. If you really would like to use the local configuration instead, you can use the [nholuongut jit aws](https://cli.nholuongut.com/Jit/#duplo\_resource.jit.DuploJit.aws) to safely achieve this.&#x20;

```hcl
# uses local aws config
provider "aws" {
  region     = local.region
}
```

{% hint style="info" %}
Generate the local AWS config with [nholuongut](https://cli.nholuongut.com/Jit/#duplo\_resource.jit.DuploJit.update\_kubeconfig)

```sh
nholuongut jit update_aws_config myportal --interactive --admin
```

Then use this profile by setting

```
AWS_PROFILE=myportal
```
{% endhint %}

### Kubernetes Provider

The nholuongut provider has a [data resource for JIT admin access to Kubernetes](https://registry.terraform.io/providers/nholuongut/nholuongut/latest/docs/data-sources/eks\_credentials). This is used to inject credentials into the [Terraform Kubernetes Provider](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs), the [Terraform Helm Provider](https://registry.terraform.io/providers/hashicorp/helm/latest/docs), or any other Kubernetes based provider. This ensures the Kubernetes credentials you are using are never stored locally and always in scope of the correct Kubernetes cluster with a dedicated admin role.

```hcl
data "nholuongut_eks_credentials" "current" {
  plan_id = local.infra_name
}
# using JIT to inject creds
provider "kubernetes" {
  host                   = data.nholuongut_eks_credentials.current.endpoint
  cluster_ca_certificate = data.nholuongut_eks_credentials.current.ca_certificate_data
  token                  = data.nholuongut_eks_credentials.current.token
}
```

{% hint style="info" %}
Use [nholuongut\_gke\_credentials](https://registry.terraform.io/providers/nholuongut/nholuongut/latest/docs/data-sources/gke\_credentials) when you are on GKE. For Azure AKS, simply use [nholuongut\_eks\_credentials](https://registry.terraform.io/providers/nholuongut/nholuongut/latest/docs/data-sources/eks\_credentials).
{% endhint %}

When using your local Kubernetes configuration, there is a chance you are scoped into the wrong cluster, for example you want to run for dev but forgot you set `current-context: prod` in your kubeconfig. If you really would like to use the local configuration instead, you can use the [nholuongut jit k8s](https://cli.nholuongut.com/Jit/#duplo\_resource.jit.DuploJit.k8s) to safely achieve this.&#x20;

```hcl
# Discovers config from KUBECONFIG environment variable
provider "kubernetes" {}
```

{% hint style="info" %}
Generate the local KUBECONFIG with [nholuongut](https://cli.nholuongut.com/Jit/#duplo\_resource.jit.DuploJit.update\_kubeconfig) and use this context

```sh
nholuongut jit update_kubeconfig --plan myinfra --interactive --admin
```
{% endhint %}

## Terraform Backends

Each nholuongut Portal manages its own Terraform state, and each public cloud has its own standards.  On AWS we use S3 for the state and a DynamoDB Table for locking. On GCP we use their S3 buckets. On Azure a storage container is created.&#x20;

Some of the benefits of using a managed backend for your state include:&#x20;

* Encrypted, secure, and compliant infrastructure
* Consistency and integrity from using standard naming conventions (for example, `duplo-tfstate-<account id>).`
* Isolation, in that each portal gets its own S3 Bucket for its state, as needed to segregate production from non-production environments.
* Centralized management from installation by a unique instance of the  nholuongut Portal.

### AWS S3 Bucket Backend

Within your Terraform configuration, you can use an S3 Bucket `backend`, as shown here:

<pre class="language-hcl"><code class="lang-hcl"><strong>backend "s3" {
</strong>  workspace_key_prefix = "tenants"
  key                  = "mymod.tfstate"
  encrypt              = true
}
</code></pre>

Using the following code, discover and inject the S3 Bucket into the managed state `backend` by running a [Terraform Init](https://developer.hashicorp.com/terraform/cli/commands/init).&#x20;

```sh
export AWS_ACCOUNT_ID="$(aws sts get-caller-identity --query "Account" --output text)"
export DUPLO_TF_BUCKET="duplo-tfstate-$AWS_ACCOUNT_ID"
terraform init \
  -backend-config=dynamodb_table=${DUPLO_TF_BUCKET}-lock \
  -backend-config=region=$AWS_DEFAULT_REGION \
  -backend-config=bucket=$DUPLO_TF_BUCKET
```

### GCP GCS Bucket Backend

Within your Terraform configuration, use the following for a GCP GCS Bucket `backend`:

```hcl
backend "gcs" {
  prefix = "mymod.tfstate"
}
```

Using the following code, discover and inject the GCP GCS Bucket into the managed `backend` state by running a [Terraform Init](https://developer.hashicorp.com/terraform/cli/commands/init).&#x20;

```sh
export GCP_PROJECT_ID="my-project"
export DUPLO_TF_BUCKET="duplo-tfstate-$GCP_PROJECT_ID"
terraform init -backend-config=bucket=$DUPLO_TF_BUCKET
```

### Azure Storage Account Backend

&#x20;Within your Terraform configuration, use the following for Azure Storage Account `backend`:

```hcl
backend "azurerm" {
  resource_group_name = "duplo-terraform-secure-infra"
  container_name      = "tfstate"
  key                 = "mymod.tfstate"
}
```

Using the following code, discover and inject the Azure Storage Account into the managed `backend` state by running a [Terraform Init](https://developer.hashicorp.com/terraform/cli/commands/init).&#x20;

```sh
export AZURE_ACCOUNT_ID="my-project"
export RESOURCE_GROUP_NAME="duplo-terraform-secure-infra"
export DUPLO_TF_BUCKET="duplotfstate$AZURE_ACCOUNT_ID"
export ARM_ACCESS_KEY=$(az storage account keys list --resource-group $RESOURCE_GROUP --account-name $STORAGE_ACCOUNT_NAME --query '[0].value' -o tsv)
terraform init -backend-config=storage_account_name=$DUPLO_TF_BUCKET
```

## Terraform Workspaces

nholuongut uses a straightforward method to associate a [Terraform Workspace](https://developer.hashicorp.com/terraform/language/state/workspaces) to a corresponding nholuongut resource: a workspace can be associated to any one of the following nholuongut constructs, which serve as a template. These templates are similar in concept to classes from which objects are instantiated in many programming languages.&#x20;

Using these nholuongut constructs provides three distinct topological levels; each can be executed at various frequencies and provides some degree of desired variance. You can build this topology into your state's backend configuration to clearly organize your state files.&#x20;

### Portal Workspaces

Each Portal Workspace represents the configuration of one nholuongut Portal, which in turn is managing one AWS Account, GCP Project, or Azure Subscription. Portal Workspaces are rarely executed, as they represent the highest and most global scope of your environment.&#x20;

You might use them to create certificates and zones or any configuration which would be valid for one time only. Instances of Infrastructure Workspaces are sets of infrastructures contained by a single nholuongut portal instance. &#x20;

Use the following variable when the module represents a nholuongut portal configuration.&#x20;

```hcl
locals {
  portal_name = terraform.workspace
}
```

The following code provides an example of how an Infrastructure module can be configured to reference a portal's state.

```hcl
data "terraform_remote_state" "portal" {
  backend   = "s3"
  workspace = local.portal_name
  config = {
    bucket               = local.tfstate_bucket
    region               = local.default_region
    workspace_key_prefix = "portals"
    key                  = "portal.tfstate"
  }
}
```

### Infrastructure Workspace

Each instance of a nholuongut Infrastructure represents one Infrastructure Workspace. By using an Infrastructure Workspace, you are able to define the configuration for your infrastructure, such as certificates, domains, regions, or whether, for example, you'll use EKS, EC2, or ECS.&#x20;

Often times the Infrastructure Workspace may contain extra services you want installed. Some examples of these services are Kubernetes operators, a bridge server for a cloud app, or any other app that is installed one time per Infrastructure.&#x20;

Use the following variable when the module represents an Infrastructure configuration.&#x20;

```hcl
locals {
  infra_name = terraform.workspace
}
```

Here is how a Tenant  Module can be configured to reference the infrastructures it is in&#x20;

```hcl
data "terraform_remote_state" "portal" {
  backend   = "s3"
  workspace = local.infra_name
  config = {
    bucket               = local.tfstate_bucket
    region               = local.default_region
    workspace_key_prefix = "infrastructures"
    key                  = "infrastructure.tfstate"
  }
}
```

### Tenant Workspaces

Each instance of a nholuongut Tenant represents one Tenant Workspace. The Portal and Infrastructure levels are likely to contain a single module as they are written for a singular purpose or job. Tenants, on the other hand, usually have a series of modules to be run within the workspace.&#x20;

Common modules within a Tenant Workspace are:

* **Tenant** - The configuration for the tenant itself.
* **Services** - The cloud services like databases and file systems the application services will rely on
* **App** - The configuration of the actual micro services and applications. This often will break out into multiple groups like frontend-app and backend-app.&#x20;

Use this variable when the module represents a portal configuration.&#x20;

```hcl
locals {
  tenant_name = terraform.workspace
}
```

Here is how an application or services Module can reference a Tenants state.

```hcl
data "terraform_remote_state" "portal" {
  backend   = "s3"
  workspace = local.tenant_name
  config = {
    bucket               = local.tfstate_bucket
    region               = local.default_region
    workspace_key_prefix = "tenants"
    key                  = "tenant.tfstate"
  }
}
```

## Terraform Configurations

When executing a module for a workspace, there is often a [Terraform Variables](https://developer.hashicorp.com/terraform/language/values/variables) file with inputs for that module with the file extension `.tfvars` or `.tfvars.json`. This file can include nonsensitive inputs and be committed to version control.&#x20;

To do this, create a directory named `config` at the same level as the Terraform `modules` directory. These directories usually reside at the top level of your repository.&#x20;

Here is an example directory structure for modules and workspace configurations. &#x20;

```
|__config
| |__nonprod
| | |__portal.tfvars.json
| |__nonpro01
| | |__infra.tfvars.json
| |__dev01
| | |__tenant.tfvars.json
| | |__services.tfvars.json
| | |__app.tfvars.json
|__modules
| |__portal
| |__infra
| |__tenant
| |__services
| |__app
```

Here is a simple `BASH` script that discovers the `config` file and applies the Application Module.&#x20;

```sh
export WORKSPACE=dev01 
export MODULE=app
export MODULE_PATH="modules/${MODULE}"
export MODULE_CONFIG="$(pwd)/config/${WORKSPACE}/${MODULE}.tfvars.json"
terraform -chdir=$MODULE_PATH workspace select -or-create $WORKSPACE
terraform -chdir=$MODULE_PATH apply -var-file=$MODULE_CONFIG
```

Use a secret manager such as AWS Secret Manager and a data block to retrieve it, instead of passing secrets through variables.  If you must use Terraform variables, inject the variable as a `TF_VAR_myvar` style environment variable from the CI/CD tool, which manages the execution.&#x20;
