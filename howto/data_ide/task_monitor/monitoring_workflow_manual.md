# Monitoring Manual Workflow Instances

<br />

You can perform the following monitoring actions for a manual workflow.
- View the workflow instance.
- Pre-run the workflow.
- Pre-run a selected task in the workflow.
- Pre-run a selected task and its subsequent.

## Viewing a Manual Workflow

You can view the general information about a workflow and the detailed information about each task that is run in the workflow.

1. In the **EnOS Management Console** and click **Workflow Operation > Manual Scheduling**. A table of all the workflows that you have access to will be displayed.

2. (Optional) In the search field above the table, enter the task ID or name to filter the workflows in the table.

3. Click the name of a workflow to view its details. A workflow panel will be shown.

4. You can click the each task node in the workflow to view the following details.

   - **Attribute**: The task settings defined during task design.

   .. image:: media/workflow_attributes.png
      :alt: Figure: Task attributes in the workflow monitor

   - **Task Content**: The content running in the task. The information in the **Task Content** tab will vary according to the task type. 
   
   <br />

   Content of a data synchronization task:

   .. image:: media/workflow_taskcontents.png
       :alt: Figure: Task contents in the workflow monitor

   <br />

   Content of a SHELL task:

   .. image:: media/workflow_taskcontents2.png
      :alt: Figure: Task contents in the workflow monitor


## Pre-running a Workflow

To manually trigger a workflow, click **Pre-run** from the **Operations** column of the workflow and set the triggering time.

## Pre-running a Task

1. Click the name of the workflow from the table.

2. In the workflow panel, right-click the task, click **Pre-run** and set the triggering time.
