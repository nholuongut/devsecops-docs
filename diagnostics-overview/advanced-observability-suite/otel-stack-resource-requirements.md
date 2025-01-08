---
description: Prerequisite resource requirements for deploying the nholuongut OTEL stack
---

# OTEL Stack Resource Requirements

The nholuongut OpenTelemetry (OTEL) stack requires specific resources for deployment. The implementation features node-level components, deployed as DaemonSets, for telemetry collection and central observability components for data aggregation, processing, and visualization. Object storage is the backbone for retaining metrics, logs, traces, and profiling data, ensuring scalability and long-term accessibility.

## OTEL Resource Requirements

### Node-Level Components (DaemonSet)

The following components run as DaemonSets on each node in the Kubernetes cluster.

<table><thead><tr><th width="160">Component</th><th width="126">CPU Limit</th><th width="140">Memory Limit</th><th>Purpose</th></tr></thead><tbody><tr><td>alloy-logs</td><td>0.5 cores</td><td>512 MB</td><td>Log collection and forwarding</td></tr><tr><td>alloy-profiles</td><td>0.5 cores</td><td>300 MB</td><td>Continuous application profiling</td></tr><tr><td>node-exporter</td><td>0.1 cores</td><td>50 MB</td><td>Hardware and OS metrics export</td></tr><tr><td>Beyla</td><td>0.5 cores</td><td>512 MB</td><td>Automatic application instrumentation</td></tr></tbody></table>

### Central Stack Components

#### Hardware Requirements

| Configuration                | Hardware Requirements             |
| ---------------------------- | --------------------------------- |
| Recommended Configuration    | CPU: 8 cores \| Memory: 32 GB RAM |
| Minimum Viable Configuration | CPU: 4 cores \| Memory: 16 GB RAM |

#### Core Services Resource Allocation

<table><thead><tr><th width="147">Service</th><th width="148">CPU Allocation</th><th width="192">Memory Allocation</th><th>Purpose</th></tr></thead><tbody><tr><td>Loki</td><td>1-3 cores</td><td>4-12 GB</td><td>Log aggregation</td></tr><tr><td>Mimir</td><td>1-3 cores</td><td>4-12 GB</td><td>Metrics storage</td></tr><tr><td>Tempo</td><td>1-2 cores</td><td>2-8 GB</td><td>Distributed tracing</td></tr><tr><td>Pyroscope</td><td>1-2 cores</td><td>2-8 GB</td><td>Continuous profiling</td></tr></tbody></table>

#### Supporting Components

<table><thead><tr><th width="173">Component</th><th width="144">CPU Allocation</th><th width="173">Memory Allocation</th><th>Purpose</th></tr></thead><tbody><tr><td>Alloy StatefulSet</td><td>1 core</td><td>2 GB</td><td>Centralized metrics collection</td></tr><tr><td>OTEL Collector</td><td>1 core</td><td>2 GB</td><td>Telemetry processing</td></tr><tr><td>kube-state-metrics</td><td>0.1 cores</td><td>50 MB</td><td>Kubernetes object metrics</td></tr></tbody></table>

### Storage Configuration

The implementation uses object storage (e.g., S3, GCS, Azure Storage Account) for:

* Metrics storage (Mimir)
* Log storage (Loki)
* Trace storage (Tempo)
* Profile data storage (Pyroscope)
