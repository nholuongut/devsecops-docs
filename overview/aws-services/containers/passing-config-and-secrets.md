---
description: Configuration and Secret management in AWS
---

# Passing Configs and Secrets

There are many ways to pass configurations to containers at run-time. Although simple to set up, using Environmental Variables can become complex if there are too many configurations, especially files and certificates.&#x20;

In Kubernetes, you also have the option to populate environment variables from [Config Maps or Secrets](../../../kubernetes-overview/configs-and-secrets/).

## **Using AWS Services to pass configurations and secrets**

### S3 buckets

You can use an S3 Bucket to store and pass configuration to the containers:

1. [Create an S3 bucket](../s3-bucket.md) in the Tenant and add the needed configurations in an S3 Bucket as a file.
2. Set the S3 Bucket name as an Environmental Variable.
3. Create a start-up script that defines the entry point of the container to download the file from the S3 bucket into the container, referenced by the Environmental Variable. Do this by:&#x20;
   * Using a [`S3 cp`](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html) command, copying the config file in S3 to a location in the container;&#x20;
   * Running the [`S3 cp`](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html) command, parsing the file, and setting the contents as an Environment Variable.
   * Create a bash script with the S3 config predefined. When run, the script sets the EV.

#### Example: Using an S3 cp command to pass configuration from an S3 bucket&#x20;

```bash
aws s3 cp s3://$S3_BUCKET_NAME/myconfig.json /app/config/config.json
```

### SSM parameter Store

Similar to using an S3 bucket, you can create values in an SSM parameter store (navigate to **Cloud Services** -> **App Integration,** and select the **SSM Parameters** tab) and set the Name of the parameter in the Environmental Variable. You then use a startup script in the AWS CLI to pull values from SSM and set them for the application in the container, either as an Environmental Variable or as a file.

### **AWS Secrets Manager**

Use the AWS Secrets Manager to set configs and secrets in Environmental Variables. Use a container startup script in the AWS CLI to copy secrets and set them in the appropriate format in the container.&#x20;

#### Example: Using AWS Secret Manager  to set configs and secrets in Environmental Variables

```
aws secretsmanager get-secret-value --region us-west-2 
--secret-id "${ENVIRONMENT}/${PROJECT}/env" 
--query SecretString --output text | base64 -d > ${ENVIRONMENT_FILE_NAME}
```

## Using ECS Services **to pass configurations and secrets**&#x20;

Use the ECS Task Definition Secrets fields to set the configuration. For example::

```bash
[ { "Name": "X_SERVICE_TOKEN", "VALUE_FROM": "arn:aws:secretsmanager:us-west-2:xxxxxxxxxxxsecret-name-qCV1K8:X_SERVICE_TOKEN::" } ]
```

Where _`X_SERVICE_TOKEN`_ is the `Secret` defined in the JSON and _`VALUE_FROM`_ is the AWS secret ARN.

## Using Kubernetes **to pass configurations and secrets**

See the [Kubernetes Configs and Secrets](../../../kubernetes-overview/configs-and-secrets/) section.
