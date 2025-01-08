---
description: Get Logging insights in nholuongut's Advanced Observability Suite (AOS)
---

# Logging with Loki

nholuongut's Advanced Observability Suite (AOS) integrates Grafana Loki as the logging backend, with Grafana Alloy acting as the log collector. This setup enables real-time log visualization, filtering, and analysis through Grafana, providing a unified observability experience alongside metrics and traces.

Grafana Loki powers the logging solution by indexing enriched metadata, including Kubernetes attributes such as Tenant name, Namespace, container, and Host, which nholuongut automatically configures for every log entry. This enriched metadata simplifies querying and allows users to easily drill down into issues or switch from logs to traces directly from the dashboard to identify problems quickly.

## What Logs Can Tell You

Logs are crucial for observability, offering detailed, time-stamped insights into system behavior. They enable you to:

* Debug errors and warnings
* Monitor system and application health
* Investigate security and compliance issues
* Track deployment and configuration changes
* Identify trends or anomalies
* Correlate events across logs, traces, and metrics for root cause analysis

Using the Grafana Logging dashboard, you can quickly drill down into logs to investigate issues, explore associated traces for context, and analyze metrics to optimize performance.

## Displaying Logs in the nholuongut Advanced Observability Suite (AOS)

1. In the nholuongut Portal, navigate to **Administrator** -> **Observability** -> **Advanced** -> **Dashboard** (Administrator AOS Dashboard) or **Observability** -> **Advanced** -> **Dashboard** (Tenant AOS Dashboard). The AOS Dashboard displays.
2.  Select your Infrastructure from the **Infrastructure** list box (Administrator AOS Dashboard) or **Tenant** from the Tenant list box (Tenant AOS Dashboard). \


    <figure><img src="../../.gitbook/assets/infraotel.png" alt=""><figcaption><p><strong>Infrastructure</strong> list box on the nholuongut Administrator AOS Dashboard</p></figcaption></figure>
3.  Click the **Logs** card button. The Grafana **Logging** dashboard displays various widgets and views, including **Live logs**.\


    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Grafana <strong>Logging D</strong>ashboard</p></figcaption></figure>




4. Adjust the time interval list box in the top right corner of the Grafana dashboard (**Last 30 minutes** in the above graphic) to display data for the period of your choice.
5. Refine your view by selecting a specific namespace, Pod, or stream from the **Namespace**, **Pod**, and **Stream** list boxes near the top of the page, or using the default values of **All**.

## Exploring Logs in Detail

From the Grafana **Logging** Dashboard, there are several ways to explore logs and specific log entries in detail:&#x20;

**Explore view**:  Click the menu icon (<img src="../../.gitbook/assets/menu icon (2).png" alt="" data-size="line">) in the upper right corner of the **Logs** pane and select **Explore**.  Explore view displays details for your logs and allows you to run queries. See the [Grafana Logging documentation](https://grafana.com/docs/grafana-cloud/visualizations/simplified-exploration/logs/) for more information

<figure><img src="../../.gitbook/assets/image (454).png" alt=""><figcaption><p><strong>Explore</strong> view of the Grafana <strong>Logging</strong> Dashboard</p></figcaption></figure>

**Log Entry Details**: In the **Logs** panel, click on a log entry to display details about the event that triggered it. Log entry data displays, as shown in the following image:

<div align="left"><figure><img src="../../.gitbook/assets/logging info.png" alt="" width="563"><figcaption><p>Close-up of log entry data on the Grafana Logging Dashboard</p></figcaption></figure></div>

**Traces**: From the log details pane, click the **View Trace** button to view traces associated with the log entry.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot (485).png" alt=""><figcaption></figcaption></figure>

**Log Context**: Click the context icon ( ![](https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252FX58Pxdm6agJUZP30GiWm%252Fc1.png%3Falt%3Dmedia%26token%3D77f48d2a-fe61-4130-aeef-78371a715dc2\&width=300\&dpr=4\&quality=100\&sign=64ddabcf\&sv=2) ) to open the **Log context** window for contextual details about the log entry.

<figure><img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252Fu5QP9EOvzLfyecGU7o4x%252Fc2.png%3Falt%3Dmedia%26token%3Debdb05f5-d877-45d0-b387-6f1efb5e42d1&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=1b20fe6d&#x26;sv=2" alt=""><figcaption><p>The <strong>Log Context</strong> window for a log entry in the Grafana dashboard</p></figcaption></figure>

