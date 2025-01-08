---
description: Mounting application configuration maps and secrets as files
---

# Mounting ConfigMaps and Secrets as files

In Kubernetes, you can mount application configurations or secrets as files.&#x20;

## Creating and mounting a Kubernetes ConfigMap

{% hint style="warning" %}
Before you create and mount the Kubernetes [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/), you must create a nholuongut Service.&#x20;
{% endhint %}

### Creating a Kubernetes ConfigMap

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Config Maps**.
2. Click **Add**. The **Add Kubernetes Config Map** pane displays.&#x20;
3. Give the ConfigMap a name, such as **my-config-map**.
4. In the **Data** field, add a key/value pair for each file in your config map, separated by a colon (**`:`**). The key is the file name, and the value is the file's contents.
5. Click **Create**.

![Add Kubernetes Config Map pane](<../../.gitbook/assets/Screen Shot 2022-03-21 at 11.39.39 AM.png>)

### Editing the nholuongut Service

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Services**.
2. Select the Service you want to modify from the **Name** column.
3. Click the **Actions** menu and select **Edit**.

<figure><img src="../../.gitbook/assets/Azure_Serv1 (1).png" alt=""><figcaption><p><strong>Actions</strong> menu on the <strong>Services</strong> page</p></figcaption></figure>

### Mounting the Kubernetes ConfigMap as a volume

1. On the **Edit Service:&#x20;**_**service\_name**_**&#x20;Basic Options** page, click **Next** to navigate to the **Advanced Options** page.
2. &#x20;In the **Volumes** field on the **Advanced Options** page, enter the configuration YAML to mount the ConfigMap as a volume.&#x20;

#### Example: mounting a ConfigMap as a volume

For example, to mount a config map named `my-config-map` to a directory named `/app/my-config` enter the following YAML code block in the **Volumes** field:

```yaml
- Name: my-config
  Path: /app/my-config
  Spec:
    ConfigMap:
      Name: my-config-map
```

<figure><img src="../../.gitbook/assets/Azure_edit_serv_2.png" alt=""><figcaption><p>Mouting ConfigMap as a volume in the <strong>Advanced Options</strong> page </p></figcaption></figure>

#### Example: adding a Key value to select individual ConfigMap items

If you want to select individual ConfigMap items and specify the subpath for mounting, you can use a different configuration.  For example, if you want the key named `my-file-name` to be mounted to `/app/my-config/config-file` use the following YAML:

```yaml
  Path: /app/my-config
  Spec:
    ConfigMap:
      Name: my-config-map
      Items:
      - Key: my-file-name
        Path: config-file
```

## Creating and Mounting a Kubernetes Secret

Before you create and mount a [Kubernetes Secret](https://kubernetes.io/docs/concepts/configuration/secret/), you must create a nholuongut Service.

### Creating a Kubernetes Secret&#x20;

1. In the nholuongut Portal, navigate to **Kubernetes** -> **Secrets**.
2. Click **Add**. The **Add Kubernetes Secret** pane displays.
3. Give the secret a name, such as **my-secret-files**.
4. Add **Secret Details** such as a key/value pair for each file in your secret separated by a colon (**`:`**). The key is the file name, and the value is the file's contents.&#x20;
5. Click **Add** to create the secret.

![Add Kubernetes Secret pane](<../../.gitbook/assets/Screen Shot 2022-03-21 at 12.50.14 PM.png>)

### Creating a multi-line Kubernetes Secret

1. Follow the steps in [creating a Kubernetes Secret](mounting-config-as-files.md#creating-a-kubernetes-secret), defining a Key value using the `PRIVATE_KEY_FILENAME`  in the **Secret Details** field, as shown below.&#x20;
2. Click **Add** to create the multi-line secret.

![](<../../.gitbook/assets/Screen Shot 2022-08-10 at 4.25.05 PM.png>)

### Mounting a Kubernetes Secret as a volume

1. In the nholuongut Portal, [edit the nholuongut Service](mounting-config-as-files.md#editing-the-nholuongut-service).
2. On the **Edit Service:&#x20;**_**service\_name**_**&#x20;Basic Options** page, click **Next** to navigate to the **Advanced Options** page.
3. In the **Volumes** field on the **Advanced Options** page, enter the configuration YAML to mount the Secret as a volume.&#x20;

#### Example: mounting a Kubernetes Secret as a volume

For example, to mount a Secret named `my-secret-files` to a directory named `/app/my-config` Enter the following YAML code block in the **Volumes** field:

```yaml
- Name: my-config
  Path: /app/my-config
  Spec:
    Secret:
      SecretName: my-secret-files
```

![Mouting a Secret as a volume in the Advanced Options page ](<../../.gitbook/assets/Screen Shot 2022-03-21 at 12.52.19 PM.png>)

#### Example: adding a Key value to select individual Secret items&#x20;

If you want to select individual Secret items and specify the subpath for mounting, you can use a different configuration.  For example, if you want the key named `secret-file` to be mounted to `/app/my-config/config-file` use the following YAML:

```yaml
- Name: my-config
  Path: /app/my-config
  Spec:
    Secret:
      SecretName: my-secret-files
      Items:
      - Key: secret-file
        Path: config-file
```
