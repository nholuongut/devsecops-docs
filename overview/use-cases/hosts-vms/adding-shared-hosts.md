---
description: >-
  Deploy Hosts in one Tenant that can be accessed by Kubernetes (K8s) Pods in a
  separate Tenant.
---

# Adding Shared Hosts

You can enable shared Hosts in the nholuongut Portal. First, configure one Tenant to allow K8s Pods from other Tenants to run on its Host(s). Then, configure another Tenant to run its K8s Pods on Hosts in other Tenants. This allows you to break Tenant boundaries for greater flexibility.&#x20;

## Configuring Tenants to allow Host sharing

### Enabling a Tenant to allow Host sharing

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenant**.
2. From the **Tenant** list, select the name of the Tenant to which the Host is defined.&#x20;
3. Click the **Settings** tab.
4. Click **Add**. The **Add Tenant Feature** pane displays.
5. From the **Select Feature** item list, select **Allow hosts to run K8S pods from other tenants**.
6.  Select **Enable.**\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/Screenshot (270).png" alt=""><figcaption><p>The <strong>Add Tenant Feature</strong> pane filled to enable Hosts to run K8s Pods from other Tenants.</p></figcaption></figure>

    </div>
7. Click **Add**. This Tenant's hosts can now run Pods from other Tenants.\


### Enabling a Tenant to run Kubernetes Pods on another Tenant's Host

1. In the nholuongut Portal, navigate to **Administrator** -> **Tenant**.
2. From the **Tenant** list, select the name of the Tenant that will access the other Tenant's Host (the Tenant not associated with a Host).&#x20;
3. Click the **Settings** tab.
4. Click **Add**. The **Add Tenant Feature** pane displays.
5. From the **Select Feature** item list, select **Enable option to run K8S pods on any host**.
6. Select **Enable.**
7.  Click **Add**. This Tenant can now run Pods on other Tenant's Hosts.\


    <div align="left">

    <figure><img src="../../../.gitbook/assets/shot 3333.png" alt=""><figcaption><p>The <strong>Add Tenant Feature</strong> pane filled to enable running Pods on any Host. </p></figcaption></figure>

    </div>

## Creating a Service that uses a shared Host

1. From the **Tenant** list box at the top of the nholuongut Portal, select the name of the Tenant that will run K8s Pods on the shared Host.
2. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**.
3. In the **Services** tab, click **Add**. The **Add Service** window displays.
4. Fill in the **Service Name**, **Cloud**, **Platform**, and **Docker Image** fields. Click **Next**.

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.18-13_00_08.png" alt=""><figcaption><p>The filled <strong>Add Service</strong> page, Basic Options.</p></figcaption></figure>

5.  In the **Advanced Options** window, from the **Run on Any Hos**t item list, select **Yes**. \


    <div align="left">

    <figure><img src="../../../.gitbook/assets/image (364).png" alt=""><figcaption><p>The filled <strong>Add Service</strong> page, Advanced Options.</p></figcaption></figure>

    </div>
6. Click **Create**. A Service running the shared Host is created.&#x20;

