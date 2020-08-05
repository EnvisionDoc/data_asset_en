# Monitoring Workflow Instances

<br />

You can perform the following monitoring actions for a workflow instance.

- View details and logs of the instance.
- Rerun the instance.
- Stop the instance.


## Viewing Details and Logs of a Workflow Instance

1. In the **EnOS Management Console** and click **Workflow Operation > Manual Instance** or **Workflow Operation > Periodic Instance**. A table of all instances that are generated in the last 24 hours will be displayed.

2. (Optional) In the search field above the table, enter the instance ID or name to filter the instances in the table.

3. Click the name of an instance to view its details. A workflow panel will be shown.

4. You can click the each task node in the workflow to view the following details.

   - **Attribute**: The task settings defined during task design.
   - **Scheduling Log**: The scheduling log of the instance, where you can download the log for analysis.
   - **Task Content**: The content running in the task. The information in the **Task Content** tab will vary according to the task type. 

## Rerunning an Instance

An instance can be rerun when its running status is **Success**, **Failed**, **Cancelled**, or **Skipped**. Click **Rerun** to rerun the current task flow instance and its downstream nodes.

## Stopping an Instance

If the running status of the instance is **Initializing** or **Running**, you can click **Stop** to stop running the current instance immediately. Note that instances already submitted for batch data processing cannot be stopped.

<br />

As long as one node fails to run in a workflow instance, the status of the entire workflow instance fails. However, the workflow instance might not have been completed. In this case, you can stop it manually.
