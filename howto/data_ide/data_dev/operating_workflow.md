# Operating a Workflow

## Pre-running a Workflow

After creating a workflow, you can click **Pre-run** to check the operations and results of the code.

- In a periodic workflow, pre-run is designed to test the code logic.
- In a one-time workflow, each operation needs to be manually triggered.

<br />

1. Click **Pre-run** and specify the workflow triggering time.

2. Click **OK**, and the workflow instance ID will be displayed in the upper right corner of the page.

3. You can then view the instance information in **Workflow Operation**. For more information, see [Workflow Operation Overview](../task_monitor/taskmonitor_overview).

.. note:: - If a time before the current system time is selected as the trigger time, the workflow will be executed immediately to generate a running instance (viewable through **Workflow Operation**). When the workflow instance is running, the trigger time is regarded as the business time and is transmitted to the time parameter for business computing.
   - Only one instance for the same workflow is allowed to run at any one time. If the pre-run instance conflicts with the current running instance, the pre-run instance will wait till the completion of the running instance.

## Cloning a Workflow

From the directory tree, right-click the workflow and click **Clone**.

.. note:: When you clone a workflow, the resources and the upstream references of the original workflow will be cloned. However, the downstream references will not be cloned.

## Deleting a Workflow

From the directory tree, right-click the workflow and click **Delete**.

.. note:: When you delete a workflow, all the instances of the workflow are removed. You can no longer retrieve the instance details through **Workflow Operation**.

## Exporting a Workflow

You can export and save a workflow configuration for future reuse.

<br />

From the directory tree, double-click the workflow and click **Export** in the workflow panel.

<br />

A file with the `.workflow` extension will be downloaded to your local file system. An exported configuration file contains the configuration information, scheduling information, and resource packages that are used in the workflow.
