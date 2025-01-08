---
description: Support for Kubernetes Probes
---

# Probes and Health Check

## Liveness, Readiness, and Startup Probes

Liveness, Readiness, and Startup probes are well-known methods to detect Pod health in Kubernetes. They are used in regular uptime monitoring and enable initial startup health that allows rolling deploys of new service updates.

The example below will define **Liveness, Readiness,** and **Startup probes** to one service deployment.

While creating a deployment, provide the below configuration to set up probes for your service.

<pre class="language-yaml" data-title="Other Container Config"><code class="lang-yaml"># setup http livenessProbe
# To perform a probe, the kubelet sends an HTTPGET request
# Service is considered healthy when /healthz retuns success code
livenessProbe:
  httpGet:
    path: /healthz #endpoint path
    port: 8080
  initialDelaySeconds: 3  #first Liveness check to be performed after 3 seconds.
  periodSeconds: 3       #verify the liveness of the application every 3 seconds

# setup http readinessProbe
readinessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 5
  periodSeconds: 5

# setup http startupProbe
<strong>startupProbe:
</strong>  initialDelaySeconds: 1
  periodSeconds: 5
  timeoutSeconds: 1
  successThreshold: 1
  failureThreshold: 1
  exec:
    command:
      - cat
      - /etc/nginx/nginx.conf
</code></pre>

<div align="left">

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption><p>Other Container Config</p></figcaption></figure>

</div>

In addition to the `httpGet` example, TCP Probes can be configured from the **Other Container Config** field:

```yaml
readinessProbe:
  tcpSocket:
    port: 8080
  initialDelaySeconds: 5
  periodSeconds: 10
livenessProbe:
  tcpSocket:
    port: 8080
  initialDelaySeconds: 15
  periodSeconds: 20
startupProbe:
  tcpSocket:
    port: 8080
  failureThreshold: 30
  periodSeconds: 10
```

Complete details of this feature are available in the Kubernetes documentation [here](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/).

## Health Check

Enable Kubernetes Health by adding a [Load Balancer Listener with Health Check enabled](load-balancers/#adding-a-load-balancer-listener).

