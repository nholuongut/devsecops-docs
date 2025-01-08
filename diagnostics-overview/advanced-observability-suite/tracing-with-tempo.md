---
description: Exploring traces in the nholuongut Advanced Observability Suite (AOS)
---

# Tracing with Tempo

nholuongut's Advanced Observability Suite (AOS) leverages [Tempo](https://grafana.com/docs/tempo/latest/) for tracing, with [Alloy](https://grafana.com/docs/alloy/latest/) and [Beyla](https://grafana.com/docs/beyla/latest/) as the data collectors. Beyla, powered by eBPF (extended Berkeley Packet Filter), enables seamless collection of observability data directly from the system kernel without requiring application-level instrumentation. By attaching to system events like network requests and function calls, Beyla efficiently gathers metrics and traces. For more detailed trace information, users can [fine-tune their applications using the OTEL SDK](application-instrumentation.md), integrating traces into logs for enhanced observability.

## What Tracing Can Tell You

Tracing with OpenTelemetry is useful in scenarios where you want to identify, analyze, and resolve performance issues or understand the flow of requests through a distributed system. Tracing is helpful for:

* Debugging latency issues
* End-to-end visibility of requests across services
* Analyzing errors and failures
* Capacity planning and optimization
* Root Cause Analysis (RCA)
* Performance tuning new features
* Validating SLAs
* Exposing misconfigurations
* Understanding user behavior

Using OpenTelemetry with Grafana, you can collect and visualize traces alongside other observability data like metrics and logs, providing a unified view for effective troubleshooting and optimization.

## Exploring Traces in the nholuongut Advanced Observability Suite

1. In the nholuongut Portal, navigate to **Administrator** -> **Observability** -> **Advanced** -> **Dashboard** (Administrator AOS Dashboard) **or Observability** -> **Advanced** -> **Dashboard** (Tenant AOS Dashboard). The AOS Dashboard displays.
2. Select your Infrastructure from the **Infrastructure** list box (Administrator AOS Dashboard) or **Tenant** from the Tenant list box (Tenant AOS Dashboard).&#x20;
3.  Click the **Traces** card button. The Grafana **Tracing** dashboard displays.\


    <div align="left"><figure><img src="../../.gitbook/assets/image (451).png" alt=""><figcaption><p>Grafana <strong>Tracing</strong> dashboard<br></p></figcaption></figure></div>
4. Use the following functions on the Grafana **Tracing** dashboard to find and view relevant trace data. See the [Grafana documentation](https://grafana.com/docs/grafana/latest/datasources/tempo/query-editor/) for detailed instructions.&#x20;

* **Search Query Builder:** Use the search query builder to filter and find traces based on parameters like service name, duration, status codes, or custom tags. This lets you quickly narrow down the traces you're interested in and dive into specific details.
* **TraceQL:** TraceQL is a powerful query language designed to provide advanced filtering and exploration of your trace data. It lets you run more complex queries for pinpointing specific traces or span data based on conditions like service dependencies, error rates, or trace attributes.
* **Service Graph:** The Service Graph visualizes the relationships between services in your application. It shows how services communicate with one another and provides a high-level view of trace flow across your system. This view helps you identify bottlenecks or failures in service-to-service interactions.

## Inspecting Traces

When you have located a trace of interest using the steps above, you can inspect specific metrics or individual spans to understand the operations that occurred during the trace.&#x20;

1.  From the Grafana **Tracing** dashboard, click on the trace of interest. The **Trace Timeline Viewer** displays on the right side of the screen. See the [Grafana Tracing documentation](https://grafana.com/docs/grafana/latest/datasources/tempo/tracing-best-practices/) for more details.\
    &#x20;

    <div align="left"><figure><img src="../../.gitbook/assets/image (452).png" alt=""><figcaption><p>The <strong>Trace Timeline Viewer</strong> in Grafana</p></figcaption></figure></div>

### Mapping Traces to Logs, Metrics, and Profiles for Debugging

The Trace Timeline Viewer can be used to map traces with logs, metrics, and profiles. These details offer insights into timing, status, and metadata, which can help identify performance bottlenecks or failures.&#x20;

* **Trace-to-Logs**: Navigate from a trace directly to relevant logs, allowing you to correlate trace details with log data.

<figure><img src="../../.gitbook/assets/span logs.png" alt=""><figcaption><p>The Grafana trace timeline showing details and a button to open logs for the span</p></figcaption></figure>

* **Trace-to-Metrics**: Jump to metrics related to a particular exception/span to analyze rates, durations, and other key performance indicators.

<div align="left"><figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Close-up of the Grafana trace timeline with </p></figcaption></figure></div>

* **Trace-to-Profiles**: Link trace spans directly to profiling data for deeper analysis of resource usage and performance at the code level. This feature allows you to correlate traces with profiles, such as CPU or memory usage, providing fine-grained insights into your system’s behavior.

For detailed instructions on inspecting traces, spans, and associated logs, see this \
[Grafana documentation page](https://grafana.com/docs/grafana/latest/explore/trace-integration/). For more information about logging with nholuongut's AOS, see the\
[nholuongut Logging page](logging-with-loki.md).&#x20;
