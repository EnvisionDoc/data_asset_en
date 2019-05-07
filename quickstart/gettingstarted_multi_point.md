# Processing Multi-Point Data

This guide intends to help you learn how to process data of multiple measure points with the Multi-Point Aggregation template.

## Prerequisites

- Authorization to the Stream Data Processing module
- Device connection is configured with data uploading to the cloud

## Procedure

The procedure of processing data with the Multi-Point Aggregation template is as follows:

1. Design and create multiple point data processing job

2. Save and release the data processing job

3. Preview the data processing job with real-time data

4. Start the data processing job

5. Monitor the running status and results of the data processing job

## Goal and Data Preparation

**Goal**

The goal of this guide is to get the sum of the raw data ingesting points *testA_raw* and *testB_raw*, and output the sum to point *testC*.

**Data Preparation**

- Model configuration: Detailed information about the *testModel* used for this guide is as follows:

| Feature Type  | Name      | Identifier | Point Type | Data Type |
|:--------------|:----------|:-----------|:-----------|:----------|
| Measure Point | testA_raw | testA_raw  | AI         | DOUBLE    |
| Measure Point | testB_raw | testB_raw  | AI         | DOUBLE    |
| Measure Point | testC     | testC      | AI         | DOUBLE    |

- Storage configuration: Configuring data storage policy for the 3 points (as either AI raw data or AI normalized data). For more information, see [Configuring TSDB Storage](https://www.envisioniot.com/docs/data-asset/en/latest/configuring_tsdb_storage.html).

- Data ingestion: For information about data ingestion of input points *testA_raw* and *testB_raw*, see [Device Connection](https://www.envisioniot.com/docs/device-connection/en/latest/quickstart/gettingstarted_device_connection.html).

## Step 1. Develop Multi-Point Data Processing Job

1. Log in EnOS Console and click **Stream Data Processing** > **Stream Development** to view all the data processing jobs created within the organization. You can double-click a job to view and edit its configuration.

2. Click the **+** icon above the job list to create a job. Enter the name and description of the job and select *Multi-Point Merge* as the template. Optionally, you can choose to import the configuration file of an existing job to complete the configuration quickly.

3. **Triggering Mode**: Select "point" as the triggering mode, and select "LastValue" as the timing interpolation strategy.

4. **Data Processing**: Click **New Strategy** and complete the following data processing strategy configuration:

   - Output Point: Select the *testC* point to receive the output value of the data processing expression.

   - Triggering Point: Select either *testA_raw* or *testB_raw* as the triggering point. If the data of *testA_raw* arrives later than that of *testB_raw*, select *testA_raw* as the triggering point. The system will trigger the output logic when the data of testA_raw arrives.

   - Output Logic: Type data processing expression in the field and click **Check Syntax** to verify the expression. Enter the following expression for this guide:

     ```
     ${testModel::testA_raw}+${testModel::testB_raw}
     ```

## Step 2. Save and Release the Job

When the job configuration is completed, you can save and release the multi point data processing job online. See the following sample configuration:

.. image:: ../media/multi_point_strategy.png

## Step 3. Start the Job

On the **Stream Operation** page, find the released job in the table, and click the **Start** icon |start_icon| for the job in the **Operations** column to start running the data processing job.

## Step 4. View the Running Results of the Job

On the **Stream Operation** page, find the running job in the table, and click the job name to open the **Stream Details** page. You can view the following information about the data processing job:

- **Summary**: View the summary of the running job, such as the overall data processing records and the data aggregation records in a specific period.

- **Log**: Click the **View Logs** icon on the upper right corner to check the running log of the job.

- **Results**: Call the `getAssetsRawDataByTimeRange` API to get the data of point *testC*. For more information, see [Calling EnOS REST APIs](https://www.envisioniot.com/docs/app-development/en/latest/call_enos_api.html).

.. |start_icon| image:: ../media/start_icon.png

<!--end-->
