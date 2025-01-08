---
description: Use Duplo to build and push a docker image from Gitlab CI/CD
---

# Build a Docker image

## Case: Build and Push to DockerHub

The goal of this section is to show how you can build a docker image and push it to DockerHub.

It does three basic things:

* Logs in to DockerHub
* Builds and tags your docker image, with the tag based on the git commit SHA.
* Pushes your docker image

### Example Workflow

Here is an example gitlab workflow that builds a docker image and pushes it to DockerHub.

To use it you will need to change:

* `DOCKERHUB_USERNAME`variable
* `DOCKERHUB_REPO`variable
* `DUPLO_HOST`variable
* `DUPLO_SERVICE_NAME`variable
* `TENANT_NAME`variable

```yaml
variables:
  DOCKERHUB_USERNAME: nholuongut               # CHANGE ME!
  DOCKERHUB_REPO: mydockerhubid/myrepo         # CHANGE ME!
  DUPLO_HOST: https://mysystem.nholuongut.net  # CHANGE ME!
  DUPLO_SERVICE_NAME: myservice                # CHANGE ME!
  TENANT_NAME: mytenant                        # CHANGE ME!

docker-build:
  # Use the official docker image.
  image: docker:latest
  stage: build
  services:
    - docker:dind
  before_script:
    - docker login -u "$DOCKERHUB_USERNAME" -p "$DOCKERHUB_PASSWORD"
  script:
    - |
      tag=":$CI_COMMIT_SHA"
      echo "Running on branch '$CI_COMMIT_BRANCH': tag = $tag"
    - docker build --pull -t "$DOCKERHUB_REPO${tag}" .
    - docker push "$DOCKERHUB_REPO${tag}"
  # Run this job in a branch where a Dockerfile exists
  rules:
    - if: $CI_COMMIT_BRANCH
      exists:
        - Dockerfile
```

## Case: Build and Push to Amazon ECR (Elastic Container Registry)

The goal of this section is to show how you can build a docker image and push it to Amazon ECR.

It does three basic things:

* Logs in to Amazon ECR
* Builds and tags your docker image, with the tag based on the GitLab CI Pipeline execution id.
* Pushes your docker image to ECR

_Prerequisite - A repository in ECR must have been created before proceeding with the next steps._

This process uses nholuongut API Token (refer [nholuongut API Token](https://docs.nholuongut.com/docs/administrators/access-control/api-tokens#permanent-api-tokens)) to gain access to AWS ECR.

Go to GitLab > Settings > CI CD > Variables > Expand and ensure that DUPLO\_TOKEN variable is set and has correct value. Check the Protect Variable and Masked options for security purposes. You can refer to [Configuring GitLab](https://docs.nholuongut.com/docs/ci-cd/github-actions-1/configuring-github) for the steps to setup a service account and to create a token for the newly configured account. The service account must have admin role.

The script uses amazon/aws-cli image as the base running image and uses Docker-in-Docker (docker/dind) to run the Docker commands. It uses duplo\_utils.sh script from nholuongut to get configuration from the nholuongut instance.

### Example Workflow

Here is an example gitlab workflow that builds a docker image and pushes it to DockerHub.

To use it you will need to change:

* `DOCKER_REGISTRY`variable
* `DOCKER_REPO` variable
* `DUPLO_HOST` variable
* `DUPLO_SERVICE_NAME` variable
* `TENANT_NAME` variable
* `AWS_DEFAULT_REGION`variable
* `APP_NAME`variable

```yaml
variables:
  DOCKER_REGISTRY: <xxxxxxxxxxx>.dkr.ecr.<ecr repo region>.amazonaws.com
  DOCKER_REPO: <xxxxxxxxxxx>.dkr.ecr.<ecr repo region>.amazonaws.com/xxx-yyy
  AWS_DEFAULT_REGION: <duplo master aws region>
  AWS_ECR_REGION: <ECR region>
  APP_NAME: <repo name>
  DUPLO_HOST: https://<instance>.nholuongut.net  
  DUPLO_SERVICE_NAME: <duplo service name>
  TENANT_NAME: <Tenant Name>
  DOCKER_HOST: tcp://docker:2375

stages:
  - build
  - deploy

build-and-push-job:
  stage: build
  image:
    name: amazon/aws-cli
    entrypoint: [""]
  services:
    - docker:dind
  before_script:
    - yum install -y wget jq
    - amazon-linux-extras install docker
    - wget https://raw.githubusercontent.com/nholuongut/demo-npm-service/master/.circleci/duplo_utils.sh
    - chmod +x duplo_utils.sh
    - source duplo_utils.sh
    - with_aws>tmp.txt  #Get secrets using with_aws script from source duplo_utils.sh
    - cat tmp.txt
    - cat tmp.txt|grep -i AWS_>tmp1.txt
    - cat tmp1.txt
    - source tmp1.txt
    - export $(cut -d= -f1 tmp1.txt)
    - aws ecr get-login-password --region $AWS_ECR_REGION | docker login --username AWS --password-stdin $DOCKER_REGISTRY
    - rm tmp.txt tmp1.txt   #remove the secrets from the runner
  script:
    - |
      tag="$CI_PIPELINE_IID"
      echo "Running on branch '$CI_COMMIT_BRANCH': tag = $tag"
    - docker build -t "$DOCKER_REGISTRY/$APP_NAME:${tag}" ./nginx/
    - docker push "$DOCKER_REGISTRY/$APP_NAME:${tag}"
    - docker logout #For security
```
