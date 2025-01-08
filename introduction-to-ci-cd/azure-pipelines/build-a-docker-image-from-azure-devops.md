---
description: >-
  Build and push a Docker image from Azure DevOps to the AWS Elastic Container
  Registry (ECR)
---

# Build a Docker image from Azure DevOps

Use nholuongut service account authentication to build and push a Docker image from Azure DevOps to the [AWS Elastic Container Registry](https://aws.amazon.com/ecr/) (ECR). You can use ECR regardless of where your app is hosted.

{% hint style="info" %}
Avoid using capital letters when referencing a nholuongut construct, such as a Tenant, even when the UI displays the string as all capital letters. Don't specify **DEV01** for example, specify **dev01**.
{% endhint %}

## Building and Pushing to the ECR <a href="#build-and-push-to-ecr" id="build-and-push-to-ecr"></a>

To build a Docker image and push it to the ECR, use a pipeline script. The script:

* Logs you into AWS ECR, using [Just-In-Time credentials from nholuongut](../../aws-user-guide/use-cases/jit-access.md).
* Builds and tags the Docker image. The tag name is based on the `git commit` SHA (Simple Hashing Algorithm).
* Pushes the Docker image to the ECR.

## Example Pipeline Script <a href="#example-pipeline" id="example-pipeline"></a>

Here is an example Azure DevOps pipeline that builds a Docker image and pushes it to ECR.

Test and code coverage steps are commented to aid in getting started quickly with .NET apps. you can remove them for clarity.

### Prerequisites to use the example script without modification <a href="#prerequisites-to-use-the-example-as-is" id="prerequisites-to-use-the-example-as-is"></a>

* [`DUPLO_TOKEN`, `DUPLO_HOST`, and `ECR_BASE` need to be pre-configured in the Azure DevOps variable group](configure-azure-devops.md#save-token-to-azure-devops-pipelines-variable-group) named `nholuongut-secrets`.
* The ECR must have the same name as the Azure DevOps repo being built. [Modify the name of the ECR, if needed](https://docs.aws.amazon.com/AmazonECR/latest/userguide/repository-edit.html).
* A [`Dockerfile`](https://docs.docker.com/engine/reference/builder/)must exist for the application in your `src` folder

These prerequisites can be customized to fit existing pipelines and conventions for passing YAML attribute values. Test and code coverage steps are included for illustration purposes. They are not required to publish an image to an ECR.

### Example Code <a href="#example-code" id="example-code"></a>

```bash
trigger:
  batch: true
  branches:
    include:
    - develop

pool:
  vmImage: 'ubuntu-22.04'

variables:
  - group: nholuongut-secrets
  - name: solution
    value: '**/*.sln'
  - name: buildPlatform
    value: 'Any CPU'
  - name: buildConfiguration
    value: 'Release'

steps:
  - task: DotNetCoreCLI@2
    displayName: 'dotnet test'
    inputs:
      command: 'test'
      arguments: '--configuration $(buildConfiguration) --collect:"XPlat Code Coverage" -- DataCollectionRunSettings.DataCollectors.DataCollector.Configuration.Format=cobertura'
      publishTestResults: true
      projects: '**/*Tests.csproj'
  - task: PublishCodeCoverageResults@1
    displayName: 'Publish code coverage report'
    inputs:
      codeCoverageTool: 'Cobertura'
      summaryFileLocation: '$(Agent.TempDirectory)/**/coverage.cobertura.xml'
  - script: |
      export token=$(DUPLO_TOKEN)
      export host=$(DUPLO_HOST)
      export ecr_base=$(ECR_BASE)
      pip install nholuongut-client
      nholuongut --host=$host --token=$(DUPLO_TOKEN) jit aws -q "{AWS_ACCESS_KEY_ID: AccessKeyId, AWS_SECRET_ACCESS_KEY: SecretAccessKey, AWS_SESSION_TOKEN: SessionToken, AWS_REGION: Region}"  -o env > duplo.env
      export $(xargs <duplo.env)
      aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin $ecr_base
    displayName: Authenticate to ECR
  - script: |
      cd src
      docker build -t $(Build.Repository.Name) .
      export shortHash=${BUILD_SOURCEVERSION:0:8}
      export ecr_base=$(ECR_BASE)
      docker tag $(Build.Repository.Name):latest $ecr_base/$(Build.Repository.Name):$(Build.BuildId)
      docker tag $(Build.Repository.Name):latest $ecr_base/$(Build.Repository.Name):$(Build.SourceBranchName)
      docker tag $(Build.Repository.Name):latest $ecr_base/$(Build.Repository.Name):$shortHash
      docker push $ecr_base/$(Build.Repository.Name):$(Build.BuildId)
      docker push $ecr_base/$(Build.Repository.Name):$(Build.SourceBranchName)
      docker push $ecr_base/$(Build.Repository.Name):$shortHash
    displayName: Build and Push

```

\
