# Synchronizing Files from External Database to HDFS

<br />

You can synchronize files from external database to the EnOS file storage system HDFS. The below lists the external database supported currently.

- Azure Blob


## Before You Start

Ensure that you have registered the data source for the external database, and the external database has the files to be synchronized. For more information, see [Data Source Registration Overview](../data_source/datasource_overview).


## Step 1: Create a Data Synchronization Task

1. In the **EnOS Management Console**, click **Data Synchronization** from the left navigation menu and click **+** to create a data synchronization task.

2. In the **New Data Synchronization Task** window, complete the basic settings for the task.

   - **Mode**: Select **Create** to create a task from scratch. If you wish to **Import task config**, go to [Creating a Task by Importing an Existing Configuration](importing_existing_config).
   - **Name**: Enter the name of the data synchronization task.
   - **Sync Type**: Select **File stream**.
   - **Scheduling Type**: Select **Manual scheduling**.
   - **Description**: Provide a description for the data synchronization task.
   - **Select Dir**: Select the directory to save the task.

   <br />

3. Click **OK** to create the data synchronization task.


## Step 2: Select the Data Source

Select the data source of the files to be synchronized to HDFS with the steps below.

1. **Data Source Type**: Select the data source of the files to be synchronized. Currently, only Azure BLOB is supported.

2. **Data Sources**: Select the data source that is registered through [Data Source Registration Overview](../data_source/datasource_overview).

3. **Directory or File Name**: Enter the directory or file to be synchronized. Wild cards, system variables, and customized variables is supported. A directory must end with "/".

4. Click **Next** to select the target.


## Step 3: Select the Target Table

For now, the HDFS(EnOS) file storage system is the only supported type. Complete the following settings for the target table.

1. **Path**: Enter the sub-directory to store the synchronized files, which must end with "/". If you do not specify the sub-directory, the synchronized files will be stored in the root directory by default.

2. Select the **File Writing Rule**.
   - **Overwrite file with the same name**: If a file that is being synchronized has the same name with a file in the target path, the file in the target path will be overwritten.
   - **Do not overwrite file with the same name**: If a file that is being synchronized has the same name with a file in the target path, the synchronization task will be stopped immediately and the file in the target path will not be overwritten. Files that have been synchronized will be stored.

   <br />

3. Click **Next**.

## Step 4: Configure Concurrency

Select the number of concurrent connections to establish and click **Next**.

<br />

The higher the concurrency number, the larger load the database will have. When the total transmission rate is fixed, the rate of a single concurrent connection is smaller.

## Step 5: Preview and Save the Configuration

You can preview the settings of the data synchronization task, and click the **Edit** button to make changes if needed. Click **Done** to save the configuration.

.. image:: media/sync_file.png


## Next Step

Click **Pre-run** and select a triggering time to test run the data synchronization task.

<br />

After a task starts to run, an instance will be generated. You can then trace the details about the instance through **Workflow Operation**. For more information, see [Workflow Operation Overview](../data_ide/task_monitor/taskmonitor_overview).

<br />

After the files are synchronized from the source databases, you can schedule other processing tasks based on the data or files. For more information, see [Batch Processing Overview](../data_ide/dataide_overview).
