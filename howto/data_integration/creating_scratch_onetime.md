# Synchronizing Data from External Data Source to Hive (Manual Scheduling)

<br />

This section shows the steps on how to create a one-time data synchronization workflow from scratch.

## Before You Start

Ensure that you have created the target Hive table to synchronize the data to. For more information, see [Creating a Hive Table](/docs/data-asset/en/dev/howto/data_ide/data_explorer/creating_hivetable.html).

## Step 1: Create a Data Synchronization Task

1. In the **EnOS Management Console**, click **Data Synchronization** from the left navigation menu and click **+** to create a data synchronization task.

2. In the **New Data Synchronization Task** window, complete the basic settings for the task.

   - **Mode**: Select **Create** to create a task from scratch. If you wish to **Import task config**, go to [Creating a Task by Importing an Existing Configuration](importing_existing_config).
   - **Name**: Enter the name of the data synchronization task.
   - **Sync Type**: Select **Structured data**.
   - **Scheduling Type**: Select **Manual scheduling**.
   - **Description**: Provide a description for the data synchronization task.
   - **Select Dir**: Select the directory to save the task.

   <br />

3. Click **OK** to create the data synchronization task.

## Step 2: Select the Data Source

### SQL Server, MySQL, or Oracle database

If you choose to synchronize data from an SQL Server, MySQL, or Oracle database, complete the following settings.

1. **Data Sources**: Select from the list of existing data sources or add a new data source. For more information, see [Data Source Registration Overview](../data_source/datasource_overview).

2. **Source Table**: Select the table to synchronize from the database.

3. **Data Filter**: If you want to filter the data to be synchronized, provide the SQL query script. Note that you do not need to enter ``where``. For example:

   ```
   age_4 >=40
   ```

4. (Optional) Click **Data Preview**. You can then preview the filtered data to synchronize as shown in the following figure.

   .. image:: media/sql_source.png
      :alt: Figure: Preview data


5. Click **Next**.

### Text-based data in BLOB, FTP, SFTP, or S3

If you choose to synchronize data from a BLOB, FTP, SFTP, or S3 data source, EnOS will transform the text-based data into a two-dimension table according to your settings.

1. **Data Sources**: Select from the list of existing data sources or add a new data source. For more information, see [Data Source Registration howto/data_integration/di_overview.html](../data_source/datasource_overview).

2. **Directory or File Name**: Enter the directory or file to be synchronized. If the directory contains multiple files, the data records will be merged. In this case, ensure that all data in the same directory has the same columns.

3. **Column Delimiter**: Select the column delimiter that is used in the text-based data file such as tab, comma, semicolon, space, or other delimiters.

4. **Encoding**: Select the encoding format of the data file: UTF-8, GBK, or GB2312.

5. **Compression Format**: Select the compression format of the data file.

6. **Number of Header Rows Ignored**: Specify the number of header rows in the data file to be ignored when loading the data.

7. **Column Header**: Specify the header to add for the source table.

   .. image:: media/s3_source.png
      :alt: Figure: Specify source


8. (Optional) Click **Data Preview**.

9. Click **Next**.


## Step 3: Select the Target Table

For now, HIVE(EnOS) is the only supported type. Complete the following settings for the target table.
1. **Table Name**: Select the target table.

2. If the Hive table is partitioned, the partitions are automatically loaded. Specify the target partition through the following methods.

   - **Column name**: The system creates new partitions based on the values in this column. If the column is date, for example, and the column values are `20180501` and `20180502`, two partitions will be created.
   - **Fixed value**: If 2017-10-11 is entered for example, the data will be automatically synchronized to the `2017-10-11` partition of the target table.
   - **Placeholder**: You can use system reserved or custom parameters, for example, the system variable `${cal_dt}`. For more information about the usage of system variables, see [Supported System Variables](../../reference/system_variables).

   .. image:: media/sql_target.png
      :alt: Figure: Preview data


4. **Data Insertion Rule**: Specify whether to overwrite the existing data in the target table, or append the data behind the existing records.

5. Click **Next**.

## Step 4: Configure Field Mapping Between Source and Target

In this step, you will map the source fields to the target fields.

1. For each field in the **Target Field** column, click the source field from the **Source Field** column to map the source with the target.

   .. image:: media/sql_mapping.png
      :alt: Figure: Mapping fields


2. When you finish mapping all fields, click **Next**.

## Step 5: Specify Scheduling Settings

1. Click **Scheduling Config** at the right edge of the configuration panel.

2. Complete the basic settings.

   - **Owner**: Select the task owner from the list of users in the organization who have access to the Data Synchronization service. The task creator is added by default. As the creator, you cannot delete yourself. You can add other owners in the same organization.
   - **Description**: (Optional) Provide a description.
   - **Alert Mode**: Select how to alert the task owner. Email is selected by default, and cannot be unselected.
      - Email: an alert e-mail is sent to the owner when an instance meets the alert conditions.
      - SMS: To use this feature, the user's phone number must be verified during user registration. Note that the SMS alert is sent only to the task owner when an instance meets the alert conditions.


## Step 6: Specify Parameters

If parameters are used when you configure the data source and target, you need to specify their values. You can specify constants, system variables, or custom variables for a parameter.

1. Click **Parameter Config** at the right edge of the configuration panel.

2. Provide the value for each parameter that is used. For example, you may use a parameter when you set the URL to your S3 data source, where `test_list` is a parameter:

  `s3://history/log_solar_dt_change_inverter/${test_list}.each_value`

  <br />

  You can then assign values for the parameter as per the below.

  `test_list=Array[20170515,20170516,20170517,20170518,20170519,20170520]`

  <br />

  This setting will make EnOS synchronize all data from the directories as per specified by the parameter values.

<br />

You can assign system variables as parameter values. For more information, see [Supported System Variables](../../reference/system_variables).


## Step 7: Configure Running Mode

Configure the container resources that are required for running the data synchronization task by the following steps:

1. Click **Running Mode** at the right edge of the configuration panel.

2. Enter the CPU and memory for running the data synchronization task

3. If your OU has not requested for the **Batch Processing - Container** resource, click the **Resource Management** link and request for the needed resources.


## Step 8: Configure Concurrency

<br />

Select the number of concurrent connections to establish and click **Next**.

<br />

The higher the concurrency number, the larger load the database will have. When the total transmission rate is fixed, the rate of a single concurrent connection is smaller.


## Step 9: Preview and Save the Configuration

You can preview the settings of the data synchronization task, and click the **Edit** button to make changes if needed. Click **Done** to save the configuration.

## Next Step

Click **Pre-run** and select a triggering time to test run the data synchronization task.

<br />

After a task starts to run, an instance will be generated. You can then trace the details about the instance through Workflow Operation. For more information, see [Workflow Operation Overview](../data_ide/task_monitor/taskmonitor_overview).

<br />

After the data is synchronized from the data source, you can schedule other processing tasks based on the data. For more information, see [Batch Processing Overview](../data_ide/dataide_overview).
