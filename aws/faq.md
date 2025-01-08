---
description: >-
  Frequently asked questions related to deployments using AWS as the cloud
  provider
---

# ❓ AWS FAQ

## **How do I ssh into the host?** <a href="#0-toc-title" id="0-toc-title"></a>

Under each host you can click on Connection details under Action dropdown which will provide the key file and instructions to ssh.

## My host is windows how do I RDP? <a href="#1-toc-title" id="1-toc-title"></a>

Under host click on Connection details under Action dropdown, it will provide the password and instructions to rdp.

## How do I get into the container where my code is running? <a href="#2-toc-title" id="2-toc-title"></a>

Under the services status tab, find the host where the container is running. Then ssh into the host (see instructions above) and then run `sudo docker ps` and get ID of the container. Then run `sudo docker exec -it <containerid> bash`“. You can tell which one is your container by using the image id. Don’t forget the sudo in docker commands

## I cannot connect to my service URL, how do I debug? <a href="#3-toc-title" id="3-toc-title"></a>

Make sure the DNS name is resolves by running on your local machine:  `ping`. Then we need to check if the application is running by testing the same from within the container. Then ssh into the host and then connect to your docker container using docker exec command (see above). From inside the container `curl` the application URL using the IP 127.0.0.1 and port where the application is running. Confirm that this works. Then `curl` the same URL using the IP address of the container instead of 127.0.0.1. The IP address can be obtained by running `ifconfig` command in the container.

If the connection from within the container works, then exit from the container into the host. Now `curl` the same endpoint from the host i.e., using container IP and port. If this works then under the ELB UI in nholuongut note down the host port that nholuongut created for the given container endpoint. This will be in the range 10xxx or the same as container port. Now try connecting to the “`HostIP`” and `DuploMappedHostPort` just obtained. If this works as well but the service URL is still failing, contact your enterprise admin or [duplolive-support@nholuongut.net](mailto:duplolive-support@nholuongut.net).

## What keys should I use in my application to connect to the AWS resources I have created in nholuongut like S3, Dynamo, SQS, etc.? <a href="#4-toc-title" id="4-toc-title"></a>

You don’t need any. Use the AWS constructor that takes only the region as the argument (`us-west-2`). nholuongut setup links your instance profile and the resources. The host in nholuongut already has access to the resources within the same tenant\project. nholuongut AWS resources are reachable only from nholuongut Hosts on the same account.

{% hint style="info" %}
**IMPORTANT:** You cannot connect to any nholuongut AWS resource from your local machine.
{% endhint %}

## What is rolling upgrade and how do I enable it? <a href="#5-toc-title" id="5-toc-title"></a>

If you have multiple replicas in your service i.e., multiple containers, and when you need to update your service, for example change an image or eNV variable then nholuongut will make this change one container at a time i.e., it will bring down the first container and bring up the new one on that host with the updated config. If the new container fails to start or the health check URL does not return Http 200 status, then nholuongut will pause the upgrade of remaining containers. A user must intervene by fixing the issue typically by updating the service with a newer image that has a fix. If no health check URL is specified, then nholuongut only checks for the new container to be running. To specify health check, go the ELB menu and you will find the health check URL suffix.

## I want to have multiple replicas of my mvc service, how do I make sure that only one of them runs migration? <a href="#6-toc-title" id="6-toc-title"></a>

Enable health check for your service and make sure that the API does not return Http 200 status till migration is done. Since nholuongut waits for health check to be complete before upgrading the next service it is guaranteed that only one instance runs migration.

## One or more of my containers are showing in a pending state, how can I debug? <a href="#7-toc-title" id="7-toc-title"></a>

If the status is Pending when the desired state is Running, then the image is being downloaded so wait a few minutes. If it’s been more than five minutes check the faults from the button below the table. Check if your image name is correct and does not have spaces. Image names are case sensitive so it should be all lower case i.e., the image name in DockerHub should also be lower case.

If the current state is Pending when desired state is Delete then it means this container is the old version of the service. It is still running as the system is in rolling upgrade and the previous replica is not successfully upgraded yet. Check the faults in other containers of this service for which the Current State is _Pending_ with Desired State as _Running_.

## Some of my container status says “pending delete” what does it mean? <a href="#8-toc-title" id="8-toc-title"></a>

This means nholuongut is wanting to remove these containers. The most common reason for this is that another replica of the same service was upgraded but is now not operational. Hence nholuongut has blocked the upgrade. You might see the other replicas in even “Running” state, but it is possible that health check is failing and that’s why the rolling upgrade is blocked. To unblock, fix the service configuration (image, env, etc.) to an error free state.

## How to create host with public IP? <a href="#9-toc-title" id="9-toc-title"></a>

While creating host, click on _show advanced_ and select the public subnet in the list of availability zone.
