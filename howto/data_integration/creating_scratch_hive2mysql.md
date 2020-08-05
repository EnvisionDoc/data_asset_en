# Synchronizing Data From EnOS Hive to the Target Database

<br />

You can synchronize data in EnOS Hive to the target databases for data analysis.

EnOS enables the synchronization of data in EnOS Hive to the following databases.

- External MySQL database
- External PostgreSQL database

.. note:: As the Data Report service has been deprecated, the Data Synchronization service no longer supports integrating data from EnOS Hive to the ReportDB.

## Before You Start

Ensure that you have created the target table before synchronizing.

- If you are synchronizing data to an external MySQL database, you must establish and verify the connection in **Data Source Registration** and create a target table. For more information, see [Registering a MySQL or SQL Server Data Source](../data_source/connecting_mysql)

- If you are synchronizing data to an external PostgreSQL database, you must establish and verify the connection in **Data Source Registration** and create a target table. For more information, see [Registering a PostgreSQL Data Source](../data_source/connecting_postgresql)


## Step 1: Create a Data Synchronization Task

1. In the **EnOS Management Console**, click **Data Synchronization** from the left navigation menu and click **+** to create a data synchronization task.

2. In the **New Data Synchronization Task** window, complete the basic settings for the task.

   - **Mode**: Select **Create** to create a task from scratch. If you wish to **Import task config**, go to [Creating a Task by Importing an Existing Configuration](importing_existing_config).
   - **Name**: Enter the name of the data synchronization task.
   - **Sync Type**: Select **Structured data**.
   - **Scheduling Type**: Select **Manual scheduling**.
   - **Description**: Provide a description for the data synchronization task.
   - **Select Dir**: Select the directory to save the task.

3. Click **OK** to create the data synchronization task.


## Step 2: Select the Hive Data Source

To select and synchronize data to external MySQL database or PostgreSQL database, follow the steps below.

1. **Data Source Type**: Select HIVE(EnOS).

2. **Source Table**: Select the data table to be synchronized.

3. (Optional) Specify the **Partition** to be synchronized through the following methods. If not specified, all data is synchronized to the target data table.

   - Fixed value: If 20180101 is entered, for example, the data will be automatically synchronized to the `20180101` partition of the target table.
   - Placeholder: You can use system reserved or custom parameters such as the system variable `${cal_dt}`. For more information about the usage of system variables, see [Supported System Variables](../../reference/system_variables).

4. (Optional) Click **Data Preview**. The system will display 5 random data entries by default.

5. Click **Next** to select the target table.


## Step 3: Select the Target Table

You can synchronize data from Hive to an external MySQL database or PostgreSQL database.

<br />

- To synchronize the data to an external MySQL database, follow the steps below.

  1. **Data Source Type**: Select MYSQL.

  2. **Data Sources**: Select the target database that the data is synchronized to.

  3. **Table Name**: Select the target table that the data is synchronized to.

  4. **Data Writing Rule**: Select **Overwrite existing data** or **Do not overwrite existing data** according to your requirements.

  5. Click **Next**.

<br />

- To synchronize data to an external PostgreSQL database, follow the steps below.

  1. **Data Source Type**: Select POSTGRESQL.

  2. **Data Sources**: Select the target database that the data is synchronized to.

  3. **Schema**: Select the schema of the target database.

  4. **Table Name**: Select the target table that the data is synchronized to.

  5. **Data Writing Rule**: Select **Overwrite existing data** or **Do not overwrite existing data** according to your requirements.

  6. Click **Next**.

## Next Step

You can continue to configure the task scheduling settings, parameter settings, field mapping configuration, and channel control. For more information, see the following.

- Periodic scheduling: See [Synchronizing Data from External Data Source to Hive (Periodic Scheduling)](creating_scratch_periodic#step-4-configure-field-mapping-between-source-and-target).
- Manual scheduling: See [Synchronizing Data from External Data Source to Hive (Manual Scheduling)](creating_scratch_onetime#step-4-configure-field-mapping-between-source-and-target).
