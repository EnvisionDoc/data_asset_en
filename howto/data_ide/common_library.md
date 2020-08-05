# Common Library

<br />

EnOS provides various built-in SDKs in its common library to help you access and process data more conveniently. These SDKs lower the development thresholds and improve development efficiency.

## What's Provided in the Library

.. list-table::
   :widths: 35 65

   * - SDK name
     - Description
   * - SYNC_HDFS_TO_S3
     - Synchronize data from a specified path in HDFS to a specified path in an S3 database.
   * - COLUMNS_TO_ROWS
     - Converts row data of your HIVE table, where each row contains values of all data collecting points of a device at a time, into a table where each row contains historical values of a single data collecting point.
   * - SYNC_MDM
     - Synchronizes master data to HDFS.
   * - SYNC_REPORT_DB
     - Performs one-time synchronization of full-load of data from Hive table to your target table.
   * - FLATTEN_POINTS
     - Converts EnOS raw point data (each row contains historical values of a single data collecting point) to sql-like row data (each row contains values of all data collecting points of a device at a time).
   * - POWER_DATA_INTERPOLATION
     - Interpolates power data, especially for the missing data of production.
   * - HivePartitionDroppedSDK
     - Deletes both the meta data of specified Hive partition and the stored data.
   * - SYNC_REPORT_STRUCTURE
     - Transfers table structure from Hive database, to MySQL report database.
   * - SHORT_TERM_LOAD_FORECAST
     - For different power consumers in the grid, provides 0-6 days load forecast for different-level of time granularity (15 min, 30 min, 1 hour, 1 day) based on historical data and optionally weather data.
   * - HADOOP_FILE_CRUSHER
     - Combines many small files into fewer larger files.

## How to Use the SDK

The major procedure of using the built-in SDK is as follows:

1. In **Batch Processing** > **Data Development**, browse the Common Library tree and locate the SDK that you want to use.

2. Double-click the version of the script and review the details about the script.

   .. image:: media/scenario_built-in.png
      :alt: Figure: Built-in script


3. Click **Use the SDK**.

4. In the pop-out window, provide settings about the workflow.

   .. image:: media/built-in_workflow.png
      :alt: Figure: Workflow with built-in script


5. Provide the scheduling settings. For more information, see [Creating a one-time workflow](data_dev/creating_workflow_onetime) or [Creating a periodic workflow](data_dev/creating_workflow_periodic).
