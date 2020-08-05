# Operating a Task

## Pre-running a Task

You can pre-run a single task and use this function to pinpoint issues with the task.

1. Right click a task and click **Pre-run the node** and specify the workflow triggering time.

2. Click **OK**, and the workflow instance ID will be displayed in the upper right corner of the page.

3. You can then view the instance information in **Workflow Operation**.

.. note:: - If a time before the current system time is selected as the trigger time, the workflow will be executed immediately to generate a running instance (viewable through **Workflow Operation**). When the workflow instance is running, the trigger time is regarded as the business time and is transmitted to the time parameter for business computing.
   - Only one instance for the same workflow is allowed to run at a time. If the pre-run instance conflicts with the current running instance, the pre-run instance will wait till the completion of the running instance.

## Pre-running a Task and Its Downstream

You can pre-run a task and its downstream according to your needs. Note that the **True** and **False** conditions take effect in this case. When the relation from the current task to the subsequent task is false, the subsequent task is not run.

1. Right click a task and click **Pre-run the node and downstream nodes** and specify the workflow triggering time.

2. Click **OK**, and the workflow instance ID will be displayed in the upper right corner of the page.

3. You can then view the instance information in **Workflow Operation**.


## Cloning a Task

1. Right-click the task and click **Copy**.

2. Move the cursor to a new position and click **Paste**.

## Deleting a Task

Right-click the task and click **Delete**.

When you delete a task, all its relations will be removed.
