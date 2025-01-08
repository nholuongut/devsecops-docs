---
description: Instrument applications in nholuongut using Grafana Beyla and OpenTelemetry
---

# Application Instrumentation

nholuongut leverages automated instrumentation with [Grafana Beyla](https://grafana.com/docs/beyla/latest/) and the [OpenTelemetry Operator](https://opentelemetry.io/docs/kubernetes/operator/) to provide robust monitoring and tracing without extensive manual configuration. With Grafana Beyla, users get automatic instrumentation out of the box for a wide range of languages, capturing key metrics and trace spans with minimal setup. For languages and use cases not covered by Beyla, users can manually instrument their applications using OpenTelemetry, offering full flexibility to capture detailed telemetry data where automated options are unavailable.

## Automated instrumentation using Beyla

* **Grafana Beyla** is an open-source, eBPF-based auto-instrumentation tool designed to simplify the collection of key observability data for applications written in Go, C/C++, Rust, Python, Ruby, Java, NodeJS, .NET, and more.
* It uses eBPF technology to capture RED metrics (Rate, Error, Duration) and basic trace spans for HTTP/S and gRPC services running on Linux, without requiring code changes or configuration updates.
* Beyla is ideal for getting started quickly with observability and provides a low-overhead way to monitor application performance.

For more information, see the [Beyla documentation](https://grafana.com/oss/beyla-ebpf/).&#x20;

## **OpenTelemetry Operator for Advanced Tracing**

While Beyla captures foundational metrics and spans out of the box, it does not provide distributed tracing or detailed trace spans. To address this, nholuongut integrates the Kubernetes OpenTelemetry Operator.

* This operator enables auto-instrumentation for services written in .NET, Java, Node.js, Python, and Go based on **Pod Annotations**.
* nholuongut ships an **Instrumentation object** in the OTEL namespace by default, forwarding telemetry data to an OpenTelemetry Collector (Alloy).
* The following annotations are used for different programming languages to enable automatic instrumentation:
  * .NET: `instrumentation.opentelemetry.io/inject-dotnet: "`duploservices-<\<Opentelemetry\_tenant>>/otel-instrumentation`"`
  * Go: `instrumentation.opentelemetry.io/inject-go: "`duploservices-<\<Opentelemetry\_tenant>>/otel-instrumentation`"`
  * Java: `instrumentation.opentelemetry.io/inject-java: "`duploservices-<\<Opentelemetry\_tenant>>/otel-instrumentation`"`
  * Node.js: `instrumentation.opentelemetry.io/inject-nodejs: "`duploservices-<\<Opentelemetry\_tenant>>/otel-instrumentation`"`
  * Python: `instrumentation.opentelemetry.io/inject-python: "`duploservices-<\<Opentelemetry\_tenant>>/otel-instrumentation`"`
* Users can also customize or add OpenTelemetry environmental variables for their Pods, as needed. See the [OpenTelemetry documentation](https://opentelemetry.io/docs/kubernetes/operator/automatic/) for details.&#x20;

## Manual instrumentation

For unsupported languages or use cases not covered by automated tools, manual instrumentation is recommended.

OpenTelemetry provides libraries and documentation to help developers instrument applications manually for a wide range of languages and frameworks. See the [OpenTelemetry documentation](https://opentelemetry.io/docs/languages/) for more information.&#x20;
