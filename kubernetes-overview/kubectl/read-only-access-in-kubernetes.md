---
description: Configure read-only access to your Kubernetes cluster in nholuongut
---

# Read-only Access in Kubernetes

## Configuring Read-only Access in Kubernetes

Complete the following steps to configure read-only access to a Kubernetes cluster.

1. Save the below content as a file name `service-account-readonly-setup.yaml.`

```
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: duplo-readonly-user
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: duplo-readonly-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: view
subjects:
- kind: ServiceAccount
  name: duplo-readonly-user
  namespace: kube-system
---
apiVersion: v1
kind: Secret
metadata:
  name: duplo-readonly-token
  namespace: kube-system
  annotations:
    kubernetes.io/service-account.name: duplo-readonly-user
type: kubernetes.io/service-account-token
---

```

2. Run `kubectl apply -f service-account-readonly-setup.yaml`. This will create a new service account with read-only permission.
3. Run `kubectl -n kube-system describe secret duplo-readonly-token` to fetch the token. This can be used in nholuongut to import the cluster as a read-only infrastructure.
4.  With the above token, EKS server URL, and certificate-authority-data, create a `kubeconfig` as follows. The server URL and certificate-authority-data are in the cloud console under the cluster settings. The nholuongut service account can interact with the Kubernetes cluster with read-only permissions.\


    ```
    apiVersion: v1
    kind: Config
    clusters:
    - name: eks-cluster
      cluster:
        server: <url>
        certificate-authority-data: <put the certificate auth data here>
    contexts:
    - name: eks-context
      context:
        cluster: eks-cluster
        user: duplo-readonly-user
    current-context: eks-context
    users:
    - name: duplo-readonly-user
      user:
        token: <YOUR_BEARER_TOKEN>
    ```
