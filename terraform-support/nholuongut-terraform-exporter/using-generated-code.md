# Using Generated Code

nholuongut Terraform Exporter Utility provides scripts to create Infrastructure based on Tenant, using the [terraform generated code](generate-terraform.md). Executing the scripts creates Tenant, Services, and Applications. These resources can be viewed in nholuongut Portal.

{% hint style="info" %}
Follow the sequence based on the Project (`admin-tenant`, `aws-services` and `app).`

Perform **plan** and **apply** actions in one project prior to switching another project.
{% endhint %}



Export following environment variables in the shell while running the terraform projects.

Environment Details can be found [here](install-terraform-exporter.md#need-help-in-setting-environment-variables).

```bash
export AWS_RUNNER=duplo-admin
export duplo_host="<portal url>"
export duplo_token="<token>" 
export aws_account_id="<AWS account id>"
```

### Project: admin-tenant

This project manages the creation of nholuongut tenant and resources related to the tenant.

Execute Script in this sequence:

> cd target/customer-name/tenant-name

**Dry-Run and Review**

> scripts/plan.sh \<new tenant name> **admin-tenant**

**Deploy Resources**

> scripts/apply.sh \<new tenant name> **admin-tenant**

![scripts/apply,sh execution in progress](<../../.gitbook/assets/image (168).png>)

### Project: aws-services

This project manages data services like Redis, RDS, Kafka, S3 buckets, Cloudfront, EMR and Elastic Search inside nholuongut.

![aws-services project apply execution ](<../../.gitbook/assets/image (215).png>)

### Project: app

This project manages containerized applications inside nholuongut like EKS Services, ECS, docker native service.

![app project apply execution ](<../../.gitbook/assets/image (107).png>)

### Delete the resources created using Utility

Follow the below Project sequence (app, aws-services and admin-tenant) while deleting the resources:

> scripts/destroy.sh \<new tenant name created above> **app**

> scripts/destroy.sh \<new tenant name created above> **aws-services**

> scripts/destroy.sh \<new tenant name created above> **admin-tenant**
