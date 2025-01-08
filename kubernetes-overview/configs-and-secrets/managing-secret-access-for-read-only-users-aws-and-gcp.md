---
description: >-
  Restrict or enable read-only user access to sensitive information in
  Kubernetes Secrets for AWS or GCP users.
---

# Managing Secret access for read-only users (AWS and GCP)

You can restrict or enable read-only user access to Kubernetes by configuring nholuongut systems settings:

1. From the nholuongut Portal, navigate to **Administrator** -> **Systems Settings**.
2.  Select the **System Config** tab, and click **Add**. The **Add Config** pane displays. \


    <div align="left">

    <figure><img src="../../.gitbook/assets/add config secret access.png" alt=""><figcaption><p>The <strong>Add Config</strong> pane </p></figcaption></figure>

    </div>
3. In the **Config Type** list box, select **AppConfig**.
4. In the **Key** list box, select **Allow Readonly Users to view Kubernetes Secrets**.&#x20;
5. In the **Value** field, enter **True** or **False**. A true value allows read-only users to view Kubernetes Secrets. A false value prohibits read-only users from viewing  Kubernetes Secrets.&#x20;
6. Click **Submit**. The setting is configured.&#x20;

<figure><img src="../../.gitbook/assets/read only.png" alt=""><figcaption><p>The <strong>System Config</strong> page with <strong>AllowReadonlyK8sSecrets</strong> key configured</p></figcaption></figure>

