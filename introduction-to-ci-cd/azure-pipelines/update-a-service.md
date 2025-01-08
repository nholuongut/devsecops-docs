---
description: Update the container image used by a nholuongut Service
---

# Update a Service

Use nholuongut service account authentication from Azure DevOps to update the container image used by a service.

## Updating a Service

Update a nholuongut service from an Azure DevOps pipeline using a pipeline script.

## Example Pipeline Script <a href="#example-pipeline" id="example-pipeline"></a>

Here is an example Azure DevOps pipeline that updates a Docker container image used by a nholuongut Service.

## Example Pipeline

### Prerequisites to use the example script without modification <a href="#prerequisites-to-use-the-example-as-is" id="prerequisites-to-use-the-example-as-is"></a>

* [`DUPLO_TOKEN`, `DUPLO_HOST`, and `ECR_BASE` need to be pre-configured in the Azure DevOps variable group](configure-azure-devops.md#save-token-to-azure-devops-pipelines-variable-group) named `nholuongut-secrets`
* The ECR must have the same name as the Azure DevOps repo being built. [Modify the name of the ECR, if needed.](https://docs.aws.amazon.com/AmazonECR/latest/userguide/repository-edit.html)
* Ensure that the nholuongut Service has the same name as the Azure DevOps repo being built.&#x20;

These prerequisites can be customized to fit existing pipelines and conventions for passing YAML attribute values. Note that the `resources` section triggers the deployment when the `ecr-publish` pipeline command finishes executing. `env_names` can be a list of comma-separated values for multi-deployments. Default values in early non-production environments are suitable for continuous deployment when used with the pipeline resource trigger.

### Example Code <a href="#example-code-1" id="example-code-1"></a>

```bash
parameters:
- name: tag_choice
  displayName: Tag (Build ID or short commit hash or branch name) or this-commit or this-branch
  type: string
  default: this-commit
- name: env_names
  displayName: nholuongut environment/tenant names
  type: string
  default: dev01,staging01

variables:
  - group: nholuongut-secrets

trigger: none

resources:
  pipelines:
  - pipeline: ecr-publish
    source: \api\api-ecr-publish
    trigger: 
      branches:
        include:
          - develop

steps:
  - script: |
      export tag_choice=${{ parameters.tag_choice }}
      export env_names=${{ parameters.env_names }}
      export service_name=$(Build.Repository.Name)
      echo $tag_choice
      if [ $tag_choice = 'this-commit' ]; then
        export tag_choice=${BUILD_SOURCEVERSION:0:8}
      fi
      if [ $tag_choice = 'this-branch' ]; then
        export tag_choice=$(Build.SourceBranchName)
      fi
      echo $tag_choice
      export token=$(DUPLO_TOKEN)
      export host=$(DUPLO_HOST)
      export ecr_base=$(ECR_BASE)
      echo $tenant
      pip install nholuongut-client
      export IFS=","
      for env_name in $env_names; do
        echo "Updating service in tenant $env_name"
        nholuongut --host=$host --token=$token --tenant=$env_name service update_image $service_name $ecr_base/$(Build.Repository.Name):$tag_choice
      done
    displayName: Update service image
```
