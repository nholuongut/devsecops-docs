# ECS Autoscaling

ECS Autoscaling has the ability to scale the desired count of tasks for the ECS Service configured in your infrastructure. Average CPU/Memory metrics of your tasks are used to increase/decrease the desired count value.

## Step 1: Add Auto-Scaling for Targets

Navigate to **Cloud Services** -> **ECS**. Select the **ECS Task Definition** where Autoscaling needs to be enabled > **Add Scaling Target**

Set the **MinCapacity** (minimum value 2) and **MaxCapacity** to complete the configuration.\


<div align="left">

<img src="../../../../.gitbook/assets/image (53).png" alt="">

</div>

## Step 2: Add Scaling Policy

Once Autoscaling for Targets is configured, Next we have to add Scaling Policy

Provide details below:

* **Policy Name** - The name of the scaling policy.
* **Policy Dimension** - The metric type tracked by the target tracking scaling policy.. Select from the dropdown
* **Target Value** -  The target value for the metric.&#x20;
* **Scalein Cooldown** - The amount of time, in seconds, after a scale in activity completes before another scale in activity can start.
* **ScaleOut Cooldown** -The amount of time, in seconds, after a scale out activity completes before another scale out activity can start.
* **Disable ScaleIn** - Disabling scale-in makes sure this target tracking scaling policy will never be used to scale in the Autoscaling group

This step creates the target tracking scaling policy and attaches it to the Autoscaling group

<div align="left">

<img src="../../../../.gitbook/assets/image (196).png" alt="">

</div>

## Step 3: View Scaling Target and Policy

View the Scaling Target and Policy Details from the nholuongut Portal. Update and Delete Operations are also supported from this view

![](<../../../../.gitbook/assets/image (182).png>)
