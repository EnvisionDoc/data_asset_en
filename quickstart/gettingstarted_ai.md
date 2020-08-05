# Getting Started: Aggregating Numeric Type Data

<br />

This section will help you learn how to process numeric type stream data with the Time Window Aggregation template.

## Prerequisites

- You are able to access the Stream Data Processing module.
- The device is connected and is sending data to the cloud.

## Procedure

1. Design and create a stream processing job.

2. Save and publish the stream processing job.

3. Start the stream processing job.

4. Monitor the running status and results of the job.

## Goal and Data Preparation

<br />

**Goal**

The goal of this guide is to get the maximum value of the *test_raw* input point every 5 minutes and output the calculated value to the output point *test_5min*.

<br />

**Data Preparation**

Model configuration: The model used in this guide (*testModel*) is configured as follows.

.. list-table::
   :header-rows: 1

   * - Feature Type
     - Name
     - Identifier
     - Point Type
     - Data Type
   * - Measurement Point
     - test_raw
     - test_raw
     - AI
     - double
   * - Measurement Point
     - test_5min
     - test_5min
     - AI
     - double


.. note:: - In this example, *test_raw* is the input point, and *test_5min* is the output point.
   - Ensure that both the input point and the output point are of the same type.
   - Storage configuration: Configure the input point *test_raw* as AI raw data and the output point *test_5min* as minute-level normalized AI data. For more information, see `Configuring TSDB Storage <../configuring_tsdb_storage>`__.  
   - Data ingestion: For information about data ingestion of input point *test_raw*, see `Quick Start: Connecting a Smart Device to EnOS Cloud </docs/device-connection/en/dev/quickstart/gettingstarted_device_connection.html>`__.


## Step 1. Create a Stream Processing Job

1. Log in to the **EnOS Management Console** and click **Stream Data Processing > Stream Development** to view all the stream processing jobs created within the organization. You can double-click a job to view and edit its configuration.

2. Click the **+** icon above the job list to create a stream processing job. Enter the name and description of the job and select *Time Window Aggregation* as the template. Alternatively, you can also choose to import the configuration file of an existing job to create a new job. For more details, see `Creating a Stream Processing Job <../howto/stream/creating_job>`__.

3. Configure the window strategy of the stream processing job.

   - **Window Type**: Select *Tumbling Window*, which has a fixed size and does not overlap.
   - **Latency Setting**: Select the time extension for late-arriving data. If *0 second* is selected, the late-arriving data will not be processed.

4. **Data Processing**: Click **New Strategy** to add a data processing strategy.

   - **Input Point**: Select the measurement point of the input data. In this example, select the *test_raw* point of the *testModel*.
   - **Threshold**: Specify the threshold for filtering raw data before processing.
   - **Interpolation**: Select the interpolation algorithm that is used to process the input data that exceed the threshold. Currently, the interpolation strategy only supports *Ignore*.
   - **Aggregation**: Select the function to compute the valid data in the window. The EnOS streaming processing engine currently supports functions like max, min, avg, sum, and cnt.
   - **Window Size**: Select the duration value for the time window, which specifies the amount of data to be computed in a single window.
   - **Output Point**: Select the point to receive the processed result. In this example, select the *test_5min* point.

## Step 2. Save and Publish the Job

When the stream processing configuration is completed, you can save and publish the data aggregation job online.

.. image:: ../media/ai_processing_strategy.png

## Step 3. Start the Job

On the **Stream Operation** page, find the published stream processing job in the table, and click the **Start** icon |start_icon| for the job in the **Operations** column to start running the job.

## Step 4. View the Running Results of the Job

On the **Stream Operation** page, find the running job in the table, and click the job name to open the **Stream Details** page. You can view the following information about the job.

- **Summary**: View the summary of the running job, such as the overall data processing records and the data aggregation records for a specific period.
- **Log**: Click the **View Logs** icon on the upper right corner to check the running log of the job.
- **Results**: The processed data will be stored in TSDB according to the configured storage policy. Call the corresponding API to get the stored data. For more information about data service APIs, go to **EnOS Management Console > EnOS API**.


.. |start_icon| image:: ../media/start_icon.png

<!--end-->
