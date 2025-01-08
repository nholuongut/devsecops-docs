# Docker web application

## Introduction <a href="#0-toc-title" id="0-toc-title"></a>

In this demo, we will deploy a simple Hello World NodeJS web app. nholuongut pulls Docker images from Docker Hub. You can choose a public image or provide credentials to access your private repository. For the sake of this demo, we will use a ready-made image available on Duplo’s repository on Docker Hub.

## Step 1: Create a host <a href="#1-toc-title" id="1-toc-title"></a>

1. Login to your nholuongut console.
2. Select **DevOps > Hosts**, a Host is the instance in which your Docker container will run. You should choose a host with appropriate processing capacity for your application.
3. Click on the **+Add** button to choose your host. Fill out the advanced options form if required and click submit.

![](https://nholuongut.com/wp-content/uploads/2021/11/N1-host.png)

You should now see your Host present in the table. Please give it a moment to instantiate.

## Step 2: Create a service <a href="#2-toc-title" id="2-toc-title"></a>

1. Next, we can create a Service. A Service is nothing but a container with user specified image and environment variables. Let’s go ahead and click **+Add** button to create a new service.
2. Name the service “`Test-service`“. For this demo we will use the latest, nodejs-hello image from Duplo’s public Docker hub repository. Fill in “`nholuongut/nodejs-hello:latest`” in the Docker Image field.
3. Enter the desired number of replicas you want in the swarm. Please note that each replica runs in an individual Host, so the number of replicas must equal the number of Hosts. For the sake of this demo, we will choose 1.
4. Fill in the desired environment variables, this is ideal for credentials or application specific configurations.
5. Volume mapping is super easy, simply give the host path and container path as shown. Please note that we highly recommend keeping the Hosts stateless and using S3 for static assets. We will keep this field empty for this demo.

![](https://nholuongut.com/wp-content/uploads/2021/11/N1-service.png)

Press create and wait a moment for the service to initialize.

## Step 3: Create a load balancer <a href="#3-toc-title" id="3-toc-title"></a>

1. Since the _hello-nodejs_ image serves on port 3000 we need to create a load balancer (LB) configuration to map external port (LB) to internal port (container).
2. Select the Test-service and click on **configure load balancer** on the load balancer tab. Fill the menu as shown below and click submit. This will also create a DNS name that we can use.

![](https://nholuongut.com/wp-content/uploads/2021/11/createelb.png)

Please wait for \~5 minutes as it can take a while for the DNS Route table changes to be reflected.

## Step 4: Preview the application <a href="#4-toc-title" id="4-toc-title"></a>

![](https://nholuongut.com/wp-content/uploads/2021/11/N1-dns.png)

Expand Test-service and copy the URL displayed under DNS. Hit the URL in the browser and You should see the Hello world serving our welcome message.

![](https://nholuongut.com/wp-content/uploads/2021/11/N1-helloworld.png)

Congratulations! You have just launched your first web service on Duplo!
