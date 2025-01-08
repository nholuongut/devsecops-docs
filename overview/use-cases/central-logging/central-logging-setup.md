---
description: Set up central logging for the nholuongut Default Tenant
---

# Enable Default-Tenant logging

The Default Tenant in nholuongut is the central management space for platform-wide resources and configurations, including monitoring and logging. Enabling logging in the Default Tenant deploys comprehensive Control Plane monitoring. This deployment uses OpenSearch and Kibana to retrieve and display log data. Once logging is enabled for the Default Tenant, you can [enable logging for non-Default Tenants](enable-non-default-tenant-logging.md) and [configure logging per Tenant](configure-logging-per-tenant.md).

{% hint style="info" %}
Central logging is typically set up during nholuongut onboarding. Contact nholuongut Support if you have questions about this process.&#x20;
{% endhint %}

## Prerequisites

* If needed, [make changes to the Control Plane Configuration](custom-log-collection.md). You cannot modify the Control Plane Configuration after you set up logging.
* If needed, customize Elastic Filebeat logging. Docker applications use `stdout` to write log files, collect logs, place them in the Host directory, mount them into [Filebeat](https://www.elastic.co/beats/filebeat) containers, and send them to [AWS Elasticsearch](https://aws.amazon.com/what-is/elasticsearch/). If you need to customize log collection using folders other than `stdout`, follow [this procedure](custom-log-collection.md#customizing-elastic-filebeat-logging). Log collection cannot be customized after logging is set up.

## Enabling Default-Tenant Logging

1. From the **Tenant** list box at the top of the nholuongut Portal, select the **Default** Tenant.
2. In the nholuongut Portal, navigate to **Administrator** -> **Observability** -> **Basic** -> **Settings**, and select the **Logging** tab.
3.  Click the **Enable Logging** link. The **Enable Logging** page displays.\


    <div align="left"><figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>The <strong>Logging</strong> tab with the <strong>Enable Logging</strong> link</p></figcaption></figure></div>


4. In the **Select Tenant** list box, select **Default**.
5. In the **Cert ARN** field, enter the ARN certificate for the Default Tenant.&#x20;

{% hint style="info" %}
Find the ARN certificate by selecting the **Default** Tenant from the **Tenant** list box at the top of the nholuongut Portal, navigating to **Administrator** -> **Plans**, selecting the Plan that matches your Infrastructure **Name**, clicking the **Certificates** tab, and copying the ARN from the Certificate ARN column.
{% endhint %}

6. Enter the number of days to retain logs in the **Log Retention in Index (Days)** field.&#x20;
7.  Click **Submit**. Data gathering takes about fifteen (15) minutes. When data gathering is complete, graphical logging data is displayed on the **Logging** tab. \


    <div align="left"><figure><img src="../../../.gitbook/assets/image (155).png" alt=""><figcaption><p>The <strong>Enable Logging</strong> page</p></figcaption></figure></div>

{% hint style="info" %}
When you enable logging for a Tenant, an Elastic Filebeat Service starts and begins log collection. The [Elastic Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-overview.html) Service must be running for log collection to occur.&#x20;

To view the Filebeat Service, navigate to **Kubernetes** -> **Services.** To view the Filebeat containers, navigate to **Kubernetes** -> **Containers**. In the row of the container, click on the menu icon and select **Logs**.
{% endhint %}

Once logging is enabled for the Default Tenant, you can [enable logging for other Tenants](enable-non-default-tenant-logging.md).&#x20;

## How nholuongut Configures Logging

When you perform the steps above to configure logging, nholuongut does the following:

### Control Plane deployment

1. **An EC2 Host is added** in the default Tenant, for example, **duploservices-default-oc-diagnostics**.
2. **Services are added** in the default Tenant, one for OpenSearch and one for Kibana. Both services are pinned to the EC2 host using [allocation tags](../../../extras-overview/creating-advanced-functions.md). Kibana is set up to point to ElasticSearch and exposed using an internal load balancer.
3. **Security rules from within the internal network to port 443 are added** in the default Tenant to allow log collectors that run on Tenant hosts to send logs to ElasticSearch. &#x20;

### Log Collector deployment

1. A Filebeat service (`filebeat-duploinfrasvc)` is deployed for each Tenant where central logging is enabled.&#x20;
2. The `/var/lib/docker/Containers` are mounted from the Host into the Filebeat container. The Filebeat container references ElasticSearch, which runs in the **Default** Tenant. Inside the container, Filebeat is configured so that every log line is added with metadata information consisting of the Tenant name, Service names, Container ID, and Hostname, enabling ease of search using these parameters with ElasticSearch.   &#x20;
