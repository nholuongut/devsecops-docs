---
description: Add a DaemonSet for your AWS or GCP Services in nholuongut
---

# DaemonSet

Kubernetes DaemonSets are controllers that manage Pod lifecycles, ensuring that one copy of a Pod runs on each node (or a selected subset of nodes) in the cluster. It is defined using a YAML or JSON configuration file, similar to other Kubernetes resources like Deployments or StatefulSets. See the [Kubernetes DaemonSet documentation](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) for more information.

## Creating a DaemonSet in nholuongut (AWS or GCP)

1. From the nholuongut Portal, navigate to **Kubernetes** -> **DaemonSet**, and click **Add**. The **Add DaemonSet** page displays.
2. In the **Name** field, specify a unique name for the DaemonSet.&#x20;
3. Set the **Local Tenant** toggle switch. When set to true, the Daemon set deploys only on hosts in this Tenant instead of the entire cluster.
4. In the **Configurations** field, enter the DaemonSet configurations. See the example DaemonSet JSON below.&#x20;
5. Click **Create**. The DaemonSet is created and the configurations applied.&#x20;

```json
{
   "apiVersion": "apps/v1",
   "kind": "DaemonSet",
   "metadata": {
     "name": "CUSTOMER_NAME-elasticsearch",
     "namespace": "duploservices-test31",
     "labels": {
       "k8s-app": "CUSTOMER_NAME-logging"
     }
   },
   "spec": {
     "selector": {
       "matchLabels": {
         "name": "CUSTOMER_NAME-elasticsearch"
       }
     },
     "template": {
       "metadata": {
         "labels": {
           "name": "CUSTOMER_NAME-elasticsearch"
         }
       },
       "spec": {
         "tolerations": [
           {
             "key": "node-role.kubernetes.io/control-plane",
             "operator": "Exists",
             "effect": "NoSchedule"
           },
           {
             "key": "node-role.kubernetes.io/master",
             "operator": "Exists",
             "effect": "NoSchedule"
           }
         ],
         "containers": [
           {
             "name": "CUSTOMER_NAME-elasticsearch",
             "image": "quay.io/elasticsearch/:v2.5.2",
             "resources": {
               "limits": {
                 "memory": "200Mi"
               },
               "requests": {
                 "cpu": "100m",
                 "memory": "200Mi"
               }
             }
           }
         ],
         "terminationGracePeriodSeconds": 30
       }
     }
   }
 }
```

