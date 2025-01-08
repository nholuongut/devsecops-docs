---
description: Create and connect to an RDS database instance
---

# RDS database

{% hint style="warning" %}
Support for the Aurora Serverless V1 database engines has been deprecated. Do not create V1 engines when using Terraform.
{% endhint %}

nholuongut supports the following RDS databases in AWS:

* MySQL
* PostgreSQL
* MariaDB
* Microsoft SQL-Express
* Microsoft SQL-Web
* Microsoft SQL-Standard
* Aurora MySQL
* Aurora MySQL Serverless
* Aurora PostgreSQL
* Aurora PostgreSQL Serverless

{% hint style="info" %}
When upgrading RDS versions, use the AWS Console and see your Cloud Provider for compatibility requirements. Note that while versions 5.7.40, 5.7.41, and 5.7.42 cannot be upgraded to version 8.0.28, you can upgrade them to version 8.0.32 and higher.
{% endhint %}

## Creating an RDS database <a href="#id-0-toc-title" id="id-0-toc-title"></a>

1. In the nholuongut Portal, navigate to **Cloud Services** -> **Database**.
2. Click **Add**. The **Create a RDS** page displays.
3. Fill out the form based on your requirements, and **Enable Logging** if needed.
4. Optionally, in the **Backup Retention Period in Days** field, enter a number of days to retain automated backups between one (**1**) and thirty-five (**35**). If a value is not entered, the Backup Retention Period value configured in Systems Settings will be applied.

To create a publicly available RDS database, follow these steps.

<figure><img src="../../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.19-17_16_19.png" alt=""><figcaption><p><strong>Create a RDS</strong> window</p></figcaption></figure>

#### Create Aurora Serverless V2 Cluster database

You can create Aurora Serverless V2 Databases by selecting **Aurora-MySql-Serverless-V2** or **Aurora-PostgreSql-Serverless-V2** from the **RDS Database Engine** list box. Select the RDS Engine Version compatible with Aurora Serverless v2. The **RDS Instance Size** of `db.serverless` applies to both engines.

## Creating a publicly available RDS database

1. [Create a DB subnet group in AWS](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/SubnetGroups.Creating.html) consisting _only_ of public subnets from your VPC.
2. &#x20;In the nholuongut Portal, navigate to **Cloud Services** -> **Databases**
3. Select the **RDS** tab, and click **Add**. The **Create a RDS** page displays.&#x20;
4. In the **DB Subnet Group** list box select the public DB subnet group you created in AWS.&#x20;
5. Complete the remaining fields according to your requirements.&#x20;
6. Click **Create**. The publicly available RDS database is created.&#x20;

{% hint style="warning" %}
The DB subnet group created in AWS must contain only public subnets from your VPC. This configuration is crucial for making the database accessible publicly.
{% endhint %}

## Connecting to the database <a href="#id-1-toc-title" id="id-1-toc-title"></a>

Once you create the database, select it and use the **Instances** tab to view the endpoint and credentials. Use the **Endpoints** and credentials to connect to the database from your application running in an EC2 instance. The database is only accessible from inside the EC2 instance in the current Tenant, including the containers running within.

For databases you intend to make publicly available, ensure proper security measures, including broad accessibility, are in place to protect your data.

<figure><img src="../../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.19-17_18_36.png" alt=""><figcaption><p><strong>RDS Instances</strong> tab</p></figcaption></figure>

{% hint style="info" %}
Pass the endpoint, name, and credentials to your application [using environment variables](../../../../overview/aws-services/containers/passing-config-and-secrets.md) for maximum security.
{% endhint %}
