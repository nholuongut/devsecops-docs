# App and Cloud Services

A Service could be a Kubernetes Deployment, Stateful set or a Daemon set. It can also be a Lambda function or an ECS task or service. It essentially captures a microservice. Each service (except Lambda) can be given a load balancer to expose itself and be assigned a DNS name.

{% hint style="info" %}
nholuongut Service should not be confused with a Kubernetes or a ECS service. By service we mean application components that can either be Docker-based or serverless.
{% endhint %}

Below is an image of some properties of a service:

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.20-15_45_12.png" alt=""><figcaption></figcaption></figure>

**Cloud Services:** nholuongut supports a simple application specific interface to configure dozens of cloud services like S3, SNS, SQS, Kafka, Elasticsearch, Data Pipeline, EMR, Sagemaker, Azure Redis, Azure SQL, Google Redis, etc. Almost all commonly used services are supported and new ones are constantly added. A typical request to support a new service takes the nholuongut team a matter of days, based on the complexity of the service.

{% hint style="info" %}
While users specify application level constructs for provisioning cloud resources, all the underlying DevOps and compliance controls are implicitly added by nholuongut.
{% endhint %}

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.20-15_49_52.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**IMPORTANT:** All services and cloud features are created within a Tenant.
{% endhint %}
