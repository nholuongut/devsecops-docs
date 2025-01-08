# Docker Web Application

## Introduction <a href="#id-0-toc-title" id="id-0-toc-title"></a>

In this demo, we will deploy a simple Hello World NodeJS web app. nholuongut pulls Docker images from Docker Hub. You can choose a public image or provide credentials to access your private repository. For the sake of this demo, we will use a ready-made image available on nholuongut’s repository on Docker Hub.

1. Create a new Host
2. Create a Service
3. Create a Load Balancer

## Step 1: Create a new host <a href="#id-1-toc-title" id="id-1-toc-title"></a>

1. Login to your nholuongut console.
2. Click on **Cloud Services** -> **Hosts**
3. Select the **Host** tabs. A Host is an instance in which your Docker container will run. You should choose a Host with the appropriate processing capacity for your application.

You should see the Host listed under the Hosts Listing table.

## Step 2: Create a service <a href="#id-2-toc-title" id="id-2-toc-title"></a>

1. Next, we can create a Service. A Service is nothing but a container with user-specified image and environment variables. Let’s go ahead and click the + icon to create a new service.
2. Name the service “**test-service**“. For this demo, we will use the latest, nodejs-hello image from Duplo’s public Docker hub repository. Fill in `nholuongut/nodejs-hello:latest` in the Docker Image field.
3. Enter the desired number of replicas you want in the swarm. Please note that each replica runs in an individual Host. The number of replicas must equal the number of Hosts. For the sake of this demo, we will choose 1.
4. Fill in the desired environment variables, this is ideal for credentials or application specific configurations.
5. Volume mapping is super easy, simply give the host path and container path as shown.

{% hint style="info" %}
**NOTICE:** We highly recommend keeping the Hosts stateless and using Azure Storage for static assets. We will keep this field empty for this demo.
{% endhint %}

## Step 3: Create a load balancer <a href="#id-3-toc-title" id="id-3-toc-title"></a>

Almost there. Since the hello-nodejs image serves on port 3000 we need to create a load balancer (LB) configuration to map the external port (LB) to the internal port (container).

Select the Test-service and click the plus icon on the load balancer configuration table. Fill the menu as shown below and click submit.

<div align="left">

<img src="../../.gitbook/assets/image (55).png" alt="">

</div>

Please wait for \~5 minutes as it can take a while for the Load Balancer to get provisioned.
