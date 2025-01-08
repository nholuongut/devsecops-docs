# Update Service

## Introduction

The goal of this section is to show how you can update the docker image for a service, after you have built that image.

## Example Workflow

This example makes some assumptions:

* Your workflow already has a `build` job - we created one in the previous section
* Your `build` job declares an output named `image` - also done in the previous section

To use it you will need to change:

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
  DeployToDev:
    <<: *defaults
    steps:
      - attach_workspace:
          at: ~/repo
      - run:
          name: Update Dev Environment
          command: |
            source ./.circleci/duplo_utils.sh
            tag=$(node -p "require('./package.json').version")
            update_service_rc $TENANT_NAME $tag
      - run:
          name: Verify Dev Environment
          command: |
            echo "Verifying Dev environment"
      - run:
          name: Rollback Dev
          command: |
            source ./.circleci/duplo_utils.sh
            echo "Rollback dev environment requested"
            rollback_dev
          when: on_fail
```
