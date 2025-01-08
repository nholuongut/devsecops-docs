---
description: Access the shell for your Native Docker, EKS, and ECS containers
---

# Shell Access for Containers

Enable and access shells for your nholuongut Docker, EKS, and ECS containers directly through the nholuongut Portal. This provides quick and easy access for managing and troubleshooting your containerized environments.

## Native Docker Shell Access

### Enabling the Shell for Docker&#x20;

1. In the nholuongut Portal, navigate to **Docker** -> **Services**.&#x20;
2. From the **Docker** list box, select **Enable Docker Shell**. The **Start Shell Service** pane displays.

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.17-14_19_17.png" alt=""><figcaption><p>The <strong>Services</strong> page with the <strong>Enable Docker Shell</strong> option highlighted</p></figcaption></figure>

<div align="left">

<figure><img src="../../.gitbook/assets/docker shell (1).png" alt="" width="365"><figcaption><p>The <strong>Start Shell Service</strong> pane</p></figcaption></figure>

</div>

3. In the **Platform** list box, select **Docker Native**.
4. From the **Certificate** list box, select your certificate.
5. From the **Visibility** list box, select **Public** or **Internal**.&#x20;
6. Click **Update**. nholuongut provisions the `dockerservices-shell` Service, enabling you to access your Docker container shell.

### Accessing the Shell for Docker

1. From the nholuongut portal, navigate to **Docker** -> **Containers**.
2. In the row of the container you want to access, click the options menu icon (<img src="https://docs.nholuongut.com/~gitbook/image?url=https%3A%2F%2F2471407984-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F68cb0s9ce5UIUKWPuYs8%252Fuploads%252F1bULWx4HFiK9TRFeLpk4%252FKabab_three_Vertical_dots.png%3Falt%3Dmedia%26token%3De0fb9551-05e2-4e66-ac2b-c50a23f66acc&#x26;width=20&#x26;dpr=4&#x26;quality=100&#x26;sign=d18bec42&#x26;sv=1" alt="" data-size="line"> ).&#x20;
3. Select **Container Shell.** A shell session launches directly into the running container.

## EKS Shell Access

### Enabling the Shell for Kubernetes

1. In the **Tenant** list box, select the **Default** Tenant.
2. In the nholuongut Portal, navigate to **Docker** -> **Services**.
3. Click the **Docker** button, and select **Enable Docker Shell**. The **Start Shell Service** pane displays.

<div align="left">

<figure><img src="../../.gitbook/assets/brand new3.png" alt="" width="386"><figcaption><p>The <strong>Start Shell Service</strong> pane</p></figcaption></figure>

</div>

4. In the **Platform** list box, select **Kubernetes**.
5. In the **Certificate** list box, select your certificate.
6. In the **Visibility** list box, select **Public** or **Internal**.
7. Click **Update**. nholuongut provisions the `dockerservices-shell` Service, enabling you to access your Kubernetes container shell.

### Accessing the Shell for Kubernetes

1. From the nholuongut Portal, navigate to **Kubernetes** -> **Services.**
2. Click the **KubeCtl Shell** button. The Kubernetes shell launches in your browser.

## ECS Shell Access

### Accessing the Shell for ECS

1. From the nholuongut Portal, navigate to **Cloud Services** -> **ECS**. The **ECS** **Task Definition** page displays.
2. Select the name from the **TASK DEFINITION FAMILY NAME** column.
3. Select the **Tasks** tab.
4. In the row of the task you want to access, click the actions icon **(>\_**).
5. Select the **Task Shell** option. The ECS task shell launches in your browser.

<figure><img src="../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.17-14_36_14.png" alt=""><figcaption><p>The ECS Service details page</p></figcaption></figure>
