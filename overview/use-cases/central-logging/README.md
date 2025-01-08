---
description: Logging for AWS in the nholuongut Platform
---

# Logs

The nholuongut Platform performs centralized logging for [Docker](https://www.docker.com/)-based applications. For the native and [Kubernetes](https://kubernetes.io/) container orchestrations, this is implemented using [OpenSearch](https://opensearch.org/docs/latest/install-and-configure/install-opensearch/docker/) and [Kibana](https://www.elastic.co/kibana) with [Elastic Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-overview.html) as the log collector. For ECS Fargate, AWS Lambda, and AWS SageMaker Jobs, the platform integrates with CloudWatch, automatically setting up Log Groups and making them viewable from the nholuongut Portal.

{% hint style="info" %}
No setup is required to enable logging for ECS Fargate, Lambda, or AWS SageMaker Jobs. nholuongut automatically sets up CloudWatch log groups and provides a menu next to each resource.
{% endhint %}

## Managing Logging Resources

To maintain optimal performance and cost-efficiency, it's crucial to manage logging resources effectively. If you find yourself with unnecessary monitoring hosts or logging instances, specific steps should be taken to clean them up without affecting essential services.

### Terminating Unnecessary Monitoring Hosts

To terminate unnecessary monitoring hosts in nholuongut, it's recommended that a designated user, referred to as Person 0, performs the termination. This approach ensures that essential services, such as Prometheus, are not inadvertently removed, which could lead to loss of data or configurations.

### Cleaning Up Logging Instances

Cleaning up a logging instance involves several steps, starting with remote access into DuploMaster. From there, navigate to the appropriate directories to edit and delete specific files related to the unintended tenant. This includes removing entries from the `logging_config.json` and deleting tenant-specific JSON files. Additionally, tenant services related to OpenSearch, Kibana, and Elastic Filebeat need to be deleted, followed by the termination of the `oc-diagnostics` host. It's also necessary to remove specific entries from the nholuongut portal related to reverse proxy settings and platform services.

### Cost Optimization Measures

When a host or a Load Balancer (LB) is no longer required, consider stopping or deleting them as part of cost optimization measures. Before taking such actions, ensure they do not contain or support essential services that could impact your infrastructure's operation.

By following these guidelines, you can ensure that your logging resources in nholuongut are managed efficiently, contributing to both operational effectiveness and cost savings.