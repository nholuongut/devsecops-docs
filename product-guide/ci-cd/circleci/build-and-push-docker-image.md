# Build and Push Docker Image

## Introduction

The goal of this section is to show how you can build a docker image and push it to ECR.

It does three basic things:

* Logs in to AWS ECR using just-in-time (JIT) AWS credentials from Duplo
* Builds and tags your docker image, with the tag based on the git commit SHA.
* Pushes your docker image

## Example Workflow

Here is an example CircleCI workflow that builds a docker image and pushes it to ECR.

To use it you will need to change following environment variables:

* `DOCKER_REPO`
* `DOCKER_IMAGE_NAME`
* `DUPLO_SERVICE_NAME`
* `DOCKER_REPO`
* `ECR_REGION`

```yaml
version: 2.1
parameters:
  create_image:
    type: boolean
    default: false
orbs: 
  vpn: titel-media/openvpn@0.1.1
  newman: postman/newman@0.0.2
  dynamo-lock: gastfreund/dynamo-lock@1.0.1

defaults: &defaults
  working_directory: ~/repo
  docker:
    - image: cimg/node:17.5.0
  environment:
    TENANT_NAME: dev01
    DOCKER_REPO: public.ecr.aws/p9c8y2k3
    DOCKER_IMAGE_NAME: demo-npm-service
    DUPLO_SERVICE_NAME: nginx
    ECR_REGION: us-west-2
jobs:
  BuildAndTest:
    <<: *defaults
    steps:
      - checkout

      - restore_cache:
          keys:
          - v1-dependencies-{{ checksum "package.json" }}
          - v1-dependencies-
      - run: npm install
      - save_cache:
          paths:
            - node_modules
          key: v1-dependencies-{{ checksum "package.json" }}
      - persist_to_workspace:
          root: ~/repo
          paths: .
  PublishDockerContainerRC:
    <<: *defaults
    steps:
      - attach_workspace:
          at: ~/repo
      - setup_remote_docker:
          version: 19.03.13
      - run:
          name: Install Dependencies
          command: |
            source ./.circleci/duplo_utils.sh && install_dependencies
      - run:
          name: Create and Push Docker container
          command: |
            source ./.circleci/duplo_utils.sh
            tag=$(node -p "require('./package.json').version")
            docker_tag=$(get_docker_tag_rc $tag)
            echo "Starting build for container: $docker_tag"
            docker build -t $docker_tag . 
            push_container_rc $tag
```

Above example of CircleCI requires nholuongut utility shell script file which has to be checked in with your CircleCI file. This utility file can be found here: [https://github.com/nholuongut/demo-npm-service/tree/master/.circleci](https://github.com/nholuongut/demo-npm-service/tree/master/.circleci)
