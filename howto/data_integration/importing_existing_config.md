# Creating a Task by Importing an Existing Configuration

<br />

If you have an existing task configuration that you want to reuse for the new data synchronization task, you can import the configuration file.

## Before You Start

Ensure that you have a task or workflow configuration file stored locally. For information about how to export an existing task or workflow as a configuration file, see [Exporting a Workflow](../data_ide/data_dev/operating_workflow#exporting-a-workflow).

## Procedure

1. In the **EnOS Management Console**, click **Data Synchronization** from the left navigation menu and click **+** to create a data synchronization task.

2. In the **New Data Synchronization Task** window, complete the basic settings for the task.

   - **Mode**: Select **Import task config**.
   - **Name**: Enter the name of the task.
   - **Upload File**: Browse and select the configuration file in your local file system.
   - **Sync Type**: Select whether to synchronize data or files.
   - **Scheduling Type**: Select whether to create a periodic task that is run automatically based on scheduling parameters, or a one-time task that is run only when manually triggered.
   - **Description**: Provide a description for the task.
   - **Select Dir**: Select the directory to save the task.

   <br />

3. Click **OK**.

4. Edit the settings that are loaded from the configuration file.

   - If you chose to create a periodic task in step 2, see [Synchronizing Data from External Data Source to Hive (Periodic Scheduling)](creating_scratch_periodic).
   - If you chose to create a one-time task in step 2, see [Synchronizing Data from External Data Source to Hive (Manual Scheduling)](creating_scratch_onetime).

## Next Step

Click **Pre-run** and select a triggering time to test run the data synchronization task.

<br />

After a task starts to run, an instance will be generated. You can then trace the details about the instance through **Workflow Operation**. For more information, see [Workflow Operation Overview](../data_ide/task_monitor/taskmonitor_overview).

<br />

After the data is synchronized from the data source, you can schedule other processing tasks based on the data. For more information, see [Batch Processing Overview](../data_ide/dataide_overview).
