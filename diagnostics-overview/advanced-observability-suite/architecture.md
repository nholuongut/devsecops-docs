---
description: >-
  How the Advanced Observability Suite and OpenTelemetry integrate with
  nholuongut
---

# Architecture

Advanced Observability Suite (AOS) is based on OpenTelemetry. The following graphic shows the various components.

{% hint style="info" %}
The OTel stack consists of 50 or more components and hundreds of configurations. If you need to change your OpenTelemetry configuration, contact your nholuongut support team.
{% endhint %}

<figure><img src="../../.gitbook/assets/OAS_Arch.png" alt=""><figcaption><p>nholuongut Advanced Observability Suite Architecture</p></figcaption></figure>

## Viewing the nholuongut Deployment of the OpenTelemetry Stack

To view the complete deployment of the OpenTelemetry stack:

1. In the nholuongut Portal, navigate to **Administrator** -> **Observability** -> **Advanced** -> **Dashboard**.
2. In the **Observability** area, click the **K8s/Docker** card. The Grafana K8s Resource Monitoring dashboard launches, giving you a detailed view of resources and monitoring for Kubernetes nodes, Docker containers, and Pods.

<figure><img src="../../.gitbook/assets/otel1.png" alt=""><figcaption><p>The AOS <strong>Dashboard</strong> containing the <strong>K8s/Docker</strong> card</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/garf1.png" alt=""><figcaption><p>The Grafana <strong>K8s Resource Monitoring</strong> dashboard</p></figcaption></figure>

## Viewing OpenTelemetry Data in nholuongut

OpenTelemetry data is stored in S3 Buckets, which you can view in the nholuongut Portal.

{% hint style="info" %}
OpenTelemetry data is stored in S3 Buckets in a Tenant that nholuongut preconfigures for you during Onboarding. nholuongut documentation refers to this Tenant as _**OpenTelemetry\_Tenant**_ (in bold italics), but the name may vary if a different name was chosen during setup.
{% endhint %}

1. In the nholuongut Portal, select the _**OpenTelemetry\_Tenant**_ from the **Tenant** list box at the top of the Portal.
2. Navigate to **Cloud Services** -> **Storage** and select the **S3** tab to view the data. This data setup is deployed and managed via [Flux Helm](architecture.md#viewing-the-nholuongut-deployment-of-the-opentelemetry-stack) release infrastructure.

<figure><img src="../../.gitbook/assets/S3 to edit (2).png" alt=""><figcaption><p><strong>S3 Bucket</strong> containing OpenTelemetry data in the OpenTelemetry Tenant <strong>OCT19OTEL</strong></p></figcaption></figure>

To view a complete list of Kubernetes deployments, containers, and S3 buckets in an OpenTelemetry deployment, select the _**OpenTelemetry\_Tenant**_ from the **Tenant** list box at the top of the Portal and navigate to **Kubernetes** -> **Services**.

<figure><img src="../../.gitbook/assets/image (447).png" alt=""><figcaption><p> Kubernetes deployments, containers, and S3 buckets in an OpenTelemetry deployment in Tenant <strong>OCT19OTEL</strong></p></figcaption></figure>

To view a complete list of Docker Containers in an OpenTelemetry deployment, select the _**OpenTelemetry\_Tenant**_ from the **Tenant** list box at the top of the Portal and navigate to **Kubernetes** -> **Containers**.

<figure><img src="../../.gitbook/assets/image (448).png" alt=""><figcaption><p>Docker Containers in an OpenTelemetry deployment in Tenant <strong>OCT19OTEL</strong></p></figcaption></figure>
