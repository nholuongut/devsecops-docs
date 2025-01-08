# Creating GKE Standard Cluster

When [creating an Infrastructure](./), use the **Enable GKE** toggle switch to enable GKE. In the Cluster Mode list box, select **GKE Standard**. Complete the remaining fields (**GKE Version**, **GKE Endpoint Visibility**, and **Cluster IP CIDR**). Click **Create**.

<figure><img src="../../../.gitbook/assets/image (310).png" alt=""><figcaption><p>Create Infrastructure with GKE Standard</p></figcaption></figure>

This takes about 20 minutes.  Infrastructure status should move to Completed. Once the Infrastructure status shows Complete, navigate to **Administrators** -> **Plans** to verify that a Plan has been created with the same name.

### View GKE Cluster details

You can view the details and download the kubeconfig file to connect the cluster from GKE Tab available in the infrastructure created.

<figure><img src="../../../.gitbook/assets/image (311).png" alt=""><figcaption><p>View GKE Standard Cluster</p></figcaption></figure>

