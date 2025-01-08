---
description: >-
  Schedule a Kubernetes Job in AWS and GCP by creating a Kubernetes CronJob in
  the nholuongut Portal
---

# CronJobs

A [Kubernetes ](https://kubernetes.io/)CronJob is a variant of a [Kubernetes Job](jobs.md) you can schedule to run at periodic intervals.

See the Kubernetes [CronJob](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/) documentation for more information.

## Creating a Kubernetes CronJob in the nholuongut portal

1. In the nholuongut Portal, navigate to **Kubernetes** -> **CronJob**.
2. Click **Add**. The **Add Kubernetes CronJob** page displays.
3. In the **Basic Options** step, specify the Kubernetes CronJob name.
4. In the **Schedule** field, specify the Cron Schedule in Cron Format. Click the Info Tip icon for examples. When specifying a **Schedule** in Cron Format, ensure you separate each value with a space. For example, `0 0 * * 0` is a valid Cron Format input; `00**0` is not. See the [Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/#writing-a-cronjob-spec) for detailed information about Cron Format.
5. In the **Container - 1** area, specify the **Container Name** and associated **Docker Image**.

<figure><img src="../.gitbook/assets/cron 1.png" alt=""><figcaption><p>The <strong>Add Kubernetes CronJob</strong> page with <strong>Container Nam</strong>e and <strong>Docker image</strong> fields filled.</p></figcaption></figure>

6. In the **Command** field, specify the command attributes for **Container - 1**. Click the Info Tip icon for examples. Select and copy commands as needed.

<figure><img src="../.gitbook/assets/cron retake.png" alt=""><figcaption><p>The <strong>Add Kubernetes CronJob</strong> page with the <strong>Command</strong> options window open.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/crom3.png" alt=""><figcaption><p>The <strong>Add Kubernetes CronJob</strong> page with the <strong>Command</strong> field for <strong>Container - 1</strong> filled<strong>.</strong></p></figcaption></figure>

7. To run the Kubernetes CronJob to completion, you must specify a Kubernetes [Init Container](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/).  Click the **Add Container** <img src="../.gitbook/assets/chevron_Down_arrow.png" alt="" data-size="line"> button and select the **Add Init Container** option. The **Init Container - 1** area displays.

<figure><img src="../.gitbook/assets/cron4 (1).png" alt=""><figcaption><p><strong>Add Init Container</strong> area.</p></figcaption></figure>

8. In the **Init Container - 1** area, specify the **Container Name** and associated **Docker Image**.
9. Click **Next** to open the **Advanced Configuration** step.
10. In the **Other Spec Configuration** field, specify the Kubernetes CronJob spec (in YAML) for **Init Container - 1**. Click the Info Tip icon ( <img src="../.gitbook/assets/info_tip_black.png" alt="" data-size="line"> ) for examples. Select and copy commands as needed

<figure><img src="../.gitbook/assets/cron6 (1).png" alt=""><figcaption><p>The <strong>Other Spec Configuration</strong> window on the <strong>Add Kubernetes CronJob, Advanced Configuration</strong> page<strong>.</strong></p></figcaption></figure>

<figure><img src="../.gitbook/assets/cron7.png" alt=""><figcaption><p>The <strong>Add Kubernetes CronJob</strong> page with the <strong>Other Spec Configuration</strong> field completed<strong>.</strong></p></figcaption></figure>

11. Click **Create**. The Kubernetes CronJob is created and displayed on the **CronJob** page. It will run according to the schedule you specified.&#x20;

<figure><img src="../.gitbook/assets/cron final.png" alt=""><figcaption><p><strong>K8s CronJob</strong> tab displaying Kubernetes Job <strong>CALCULATEPI.</strong></p></figcaption></figure>

## Viewing a Kubernetes CronJob&#x20;

## Managing Kubernetes CronJobs faults

You can manage/override Kubernetes Jobs faults on a Tenant or CronJob level. If a CronJob fails, and no Tenant- or Job-level fault setting is configured, nholuongut will generate a fault by default.&#x20;

### **Tenant-level Kubernetes CronJobs faults**

Enable or disable faults for failed Kubernetes CronJobs in a specific Tenant.

1. From the nholuongut Portal, navigate to **Administrator** -> **Tenant.**
2. Click the Tenant name in the **NAME** column.&#x20;
3. Select the **Settings** tab, and click **Add**. The **Add Tenant Feature** pane displays.&#x20;
4. From the **Select Feature** list box, select **Enable K8s job fault logging by default**, and use the toggle switch to enable or disable the setting.&#x20;
5.  Click **Add**. The CronJobs fault setting is added. \


    <div align="left"><figure><img src="../.gitbook/assets/tenant faults feature.png" alt=""><figcaption><p>The <strong>Add Tenant Feature</strong> pane with <strong>Enable K8s Job fault logging by default</strong> enabled</p></figcaption></figure></div>

You can view the CronJobs fault setting on the **Tenants** page (Navigate to **Administrator** -> **Tenant**, select the Tenant name) under the **Settings** tab. If the value is **true**, nholuongut will generate a fault. If the value is **false**, nholuongut will not generate a fault.&#x20;

<figure><img src="../.gitbook/assets/tenant setting set.png" alt=""><figcaption><p>The <strong>Tenant</strong> details page, <strong>Setting</strong>s tab, showing the configured Jobs fault setting</p></figcaption></figure>

### **Jobs-level Kubernetes CronJobs faults**

You can configure the faults for a specific CronJob when creating the CronJob in nholuongut. Fault settings added this way override Tenant-level settings. On the **Add Kubernetes Job** page, in the **Metadata Annotations** field, enter:&#x20;

`nholuongut.net/fault/when-failed: true.` or&#x20;

`nholuongut.net/fault/when-failed: false.`

When the value is true and the CronJob fails, nholuongut will generate a fault. When the value is false and the CronJob fails, a fault will not be generated.&#x20;

## Viewing a Kubernetes CronJob&#x20;

1. In the nholuongut Portal, navigate to **Kubernetes** -> **CronJobs**.
2. Select the Kubernetes CronJob you want to view and click the **Overview, Schedule**, and **Details** tabs for more information about the CronJob schedule and history.&#x20;

You can also view details of a Kubernetes CronJob by clicking on the **menu icon** ( <img src="../.gitbook/assets/Kabab_three_Vertical_dots (1) (1).png" alt="" data-size="line"> ) icon to the left of the job name and selecting **View**.



<figure><img src="../.gitbook/assets/cron9.png" alt=""><figcaption><p><strong>Overview</strong> tab for Kubernetes Job <strong>MYCRONJOB.</strong></p></figcaption></figure>

<figure><img src="../.gitbook/assets/cronview.png" alt=""><figcaption><p>CronJob options menu with <strong>View</strong> option highlighted.</p></figcaption></figure>

### Using the Container page to view linked Kubernetes CronJobs

You can view Kubernetes CronJobs linked to containers by clicking the container name on the **Containers** page (**Kubernetes** -> **Containers**). \


<div align="left"><figure><img src="../.gitbook/assets/j29.png" alt=""><figcaption><p>Clicking the Container <strong>Name</strong> on the <strong>Containers</strong> page to view a linked K8s CronJob</p></figcaption></figure></div>

You can filter container names by using the search field at the top of the page, as in this example:



<figure><img src="../.gitbook/assets/search containers.png" alt=""><figcaption><p>Highlighted search field on the <strong>Containers</strong> page </p></figcaption></figure>

## Editing a Kubernetes CronJob

1. In the nholuongut Portal, navigate to **Kubernetes** -> **CronJob**.
2. Select the Kubernetes CronJob you want to edit.&#x20;
3. Click the **options menu** ( <img src="../.gitbook/assets/Kabab_three_Vertical_dots (1) (1).png" alt="" data-size="line"> ) icon to the left of the Kubernetes CronJob name and select **Edit**.

You can edit and modify the following fields in the nholuongut Portal:

* **Cleanup After Finished in Seconds**
* **Other Spec Configuration**
* **Metadata Annotations**
* **Labels**

<figure><img src="../.gitbook/assets/cron edit.png" alt=""><figcaption><p>CronJob options menu with <strong>Edit</strong> option highlighted</p></figcaption></figure>

## Deleting a Kubernetes CronJob

1. In the nholuongut Portal, navigate to **Kubernetes** -> **CronJob.**
2. Select the Kubernetes CronJob you want to delete.&#x20;
3. Click the Options Menu (<img src="../.gitbook/assets/Kabab_three_Vertical_dots (1) (1).png" alt="" data-size="line">) icon to the left of the Kubernetes CronJob name and select **Delete**.

<figure><img src="../.gitbook/assets/cron delete.png" alt=""><figcaption><p>CronJob options menu with <strong>Delete</strong> option highlighted</p></figcaption></figure>

