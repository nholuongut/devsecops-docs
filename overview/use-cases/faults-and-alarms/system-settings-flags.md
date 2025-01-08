---
description: >-
  Make changes to fault settings by adding Flags under Systems Settings in the
  nholuongut portal
---

# System Settings Flags

## Disabling faults for Target Groups without instances

If there is a Target Group with no instances/targets, nholuongut generates a fault. You can configure nholuongut's Systems Settings to ignore Target Groups with no instances.

1. From the nholuongut portal, navigate to **Administrator** -> **Systems Settings**.
2. Select the **System Config** tab.
3. &#x20;Click **Add**. The **Add Config** pane displays.
4. For **ConfigType**, select **Other**.
5. In the **Other Config Type** field, type **Flags**.
6. In the **Key** field, enter **IgnoreTargetGroupWithNoInstances**.
7. In the **Value** field, enter **True**.

<div align="left">

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.27-19_27_59.png" alt=""><figcaption><p>The <strong>Add Config</strong> pane with <strong>IgnoreTargetGroupWithNoInstances</strong> Flag.</p></figcaption></figure>

</div>

8. Click **Submit**. The Flag is set and nholuongut will not generate faults for Target Groups without instances. &#x20;

<figure><img src="../../../.gitbook/assets/screenshot-nimbusweb.me-2024.02.27-19_33_44.png" alt=""><figcaption><p>The <strong>System Config</strong> page with <strong>IgnoreTargetGroupWithNoInstances</strong> set.</p></figcaption></figure>
