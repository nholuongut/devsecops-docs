---
description: >-
  Runbook to configure nholuongut Hosts with a static IP and SSH database
  tunneling for secure remote access
---

# Configuring Retool to SSH into a nholuongut Host with a Static IP Address for Secure Remote Database

This setup is useful in scenarios for nholuongut customers with external users in remote locations who need consistent, secure access to databases Hosted on nholuongut infrastructure. By configuring a public-facing nholuongut Host and attaching an Elastic IP, you provide a stable and consistent endpoint for Retool to connect to. SSH tunneling is then used to create a secure, encrypted connection between Retool and the database through the nholuongut Host. This approach ensures that even over the public internet, data transfers remain protected and private. By combining the static Elastic IP with SSH tunneling, you achieve reliable access and robust security for database interactions.

## Use this Runbook if….

Use this procedure if you are a nholuongut customer who needs secure external access to your organization’s cloud resources for:

* **Public Availability with Security:** nholuongut customers with external clients, vendors, or team members who need to interact with the database but cannot be given direct access for security reasons
* **Public Host Access with Strict Database Security:** Users who need external Host accessibility while maintaining secure strict security controls for databases.
* **Simplified Development Workflow:** Users with remote developers who need to connect to the environment without dealing with dynamic IP change and securely interact with the database for tasks like development, testing, or debugging, as if they were directly connected to the cloud network.
* **Secure Troubleshooting:** System administrators or support teams who need to quickly connect to the Host from anywhere or securely access and troubleshoot the database without exposing it to potential security risks.

## Prerequisites

* A nholuongut Host with a Public IP and network access to your database.
* A Retool account.&#x20;

## Step 1. Attaching an Elastic IP to the nholuongut Host

### Login to AWS Console

1. Navigate to [AWS Management Console](https://aws.amazon.com/).
2. Log in with your credentials.

### Allocate a New Elastic IP

1. In the AWS Console, navigate to the EC2 dashboard.
2. In the EC2 Dashboard, [Allocate an Elastic IP address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-eips.html#using-instance-addressing-eips-allocating) connected with the appropriate network (VPC).

### Associate the Elastic IP with nholuongut Host

1. Once the Elastic IP is allocated, select it from the list.
2. [Associate the Elastic IP address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-eips.html) with your nholuongut Host instance.

{% hint style="info" %}
An AWS account is needed to allocate and manage Elastic IP addresses because they are an AWS-specific service. If you're using a different cloud provider, create and associate a static IP with your nholuongut Host using their equivalent static IP addressing service.
{% endhint %}

## Step 2. Configuring SSH Access

### Log in to Retool

1. Navigate to the [Retool login page](https://login.retool.com/auth/login?source=homepage).
2. Log in with your credentials.

### Configure SSH Tunneling

1. Follow the instructions to [Configure SSH tunneling](https://docs.retool.com/data-sources/guides/connections/ssh-tunnels#configure-ssh-tunneling), being sure to:

* Enter the public IP of your nholuongut Host.
* Set the SSH port to 22 and configure it to use the private key you saved earlier.

## Step 3. Whitelisting the Retool IPs Addresses

### Log in to nholuongut

1. Navigate to the nholuongut Platform.
2. Log in with your credentials.

### Add Tenant Security Settings to Whitelist Retool IP Addresses

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenant**.
2. Select the Tenant where your host is running from the **NAME** column.
3. Select the **Security** tab and click **Add**. The **Add Tenant Security** pane displays.
4. Add the Retool IP addresses using the following inputs:

* **Source Type:** IP Address
* **IP CIDR:** Custom
* **IP Address:** Enter the [Retool CIDR IP Addresses](https://docs.retool.com/data-sources/reference/ip-allowlist-cloud-orgs) (and individual IP’s as needed).
* **Protocol:** TCP
* **Port Range:** 22

5. Click Add.&#x20;

## Summary of Steps

### 1. Attaching an Elastic IP to the nholuongut Host

* Login to AWS Console
* Allocate a New Elastic IP
* Associate the Elastic IP with nholuongut Host

### 2. Configuring SSH Access

* Log in to your Retool
* Configure SSH Tunneling

### 3. Whitelisting the Retool IPs Addresses

* Log in to nholuongut
* Add Tenant Security Settings to Whitelist Retool IP Addresses

This Runbook configures secure SSH access from Retool to a nholuongut Host by attaching an Elastic IP, setting up SSH tunneling, and whitelisting Retool IP addresses to ensure proper connectivity and security.

## Resources

Links to resources that may be helpful to users of this Runbook.&#x20;

[nholuongut documentation for creating Hosts](https://docs.nholuongut.com/docs/overview/use-cases/hosts-vms/adding-hosts).
