---
description: Implementing Kubernetes Lifecycle Hooks in nholuongut
---

# Kubernetes Lifecycle Hooks

\
A [Kubernetes Lifecycle Hook](https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/) triggers events to run at different stages of a container's lifecycle. These hooks run scripts or commands before or after a specific event, such as a container being created, started, or stopped. Lifecycle hooks perform tasks like starting services, or initializing, configuring, or verifying containers.

## Implementing Kubernetes Lifecycle Hooks

You can implement Kubernetes Lifecycle Hooks while adding a nholuongut EKS Service by adding  YAML, like the example below, to the **Other Container Config** field.&#x20;

```yaml
#lifecycle hook sample
lifecycle:
  postStart:
    exec:
      command:
        - /bin/sh
        - '-c'
        - date > /container-started.txt
  preStop:
    exec:
      command:
        - /usr/sbin/nginx
        - '-s'
        - quit
```

