# Getting Started: Querying Data Quality Report

<br />

This section will help you learn how to use the StreamSets operators for data quality tagging and then query a data quality report.

## Prerequisites
- You have applied for the Stream Data Processing resource and Time Series Database resource through Resource Management.
- You have permission to access the Data Quality module and the StreamSets feature of the Stream Data Processing module.
- The devices are connected and sending data to EnOS Cloud.

## Goals and Data Preparation

<br />

**Goal**

The goal of this guide is to quality tag the AI type measurement point *test_raw*, and query the quality report of this measurement point.

<br />

**Data Preparation**

- Model configuration: The model used in this guide (*testModel*) is configured as follows.

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
     - test_raw_filter
     - test_raw_filter
     - AI
     - double
   * - Measurement Point
     - test_raw_dq
     - test_raw_dq
     - AI
     - double

.. note:: - The *test_raw* measurement point is for ingesting raw data, the *test_raw_filter* measurement point is for receiving the data that is filtered by the specified threshold, and the *test_raw_dq* measurement point is for receiving the output of the raw data being processed by the stream processing engine with data quality tags.
     - Ensure that the both the input point and output point are of AI type.


- Data connection: See [Quick Start: Connecting a Smart Device to EnOS Cloud](/docs/device-connection/en/dev/quickstart/gettingstarted_device_connection.html) to complete the data ingestion for the *test_raw* measurement point.


## Procedure
The steps for data quality tagging and generating quality reports are as follows.
- Create and develop a stream processing job to quality tag the raw data.
- Save, publish, and start the stream processing job.
- View the data quality report.

### Step 1: Create and develop a stream processing job to quality tag the raw data.
1. Download the StreamSets pipeline configuration template from https://support.envisioniot.com/docs/data-asset/en/dev/_static/streamsets_pipeline_demo.json (right click the link and save the `streamsets_pipeline_demo.json` file to a local directory).

2. Go to **EnOS Management Console > Stream Processing > StreamSets**, click the triangle beside the **Create New Pipeline** button, and select **Import Pipeline**.
3. On the **Import Pipeline** window, enter a pipeline title and description, click **Browse ...**, navigate to and select the configuration template file, and click **Import**.
4. Enter the editor and use the following StreamSets operators to edit the stream data processing job. Configuration of the Stages are as follows:


.. list-table::
   :header-rows: 1

   * - No.
     - StreamSets Stage
     - Parameter Configuration
     - Description
   * - 1
     - Data Source
     - + Topic: MEASURE_POINT_INTERNAL     
       + Data Format: JSON

     - Configure the data source.
   * - 2
     - Point Selector
     - Select Policy: testModel::test_raw
     - Select the measurement point to be processed by the stream data processing job.
   * - 3
     - MinMax Outlier
     - + Model Point: testModel::test_raw
       + OpenClose: (x,y)
       + Min-Max: 0,90.00
       + Output PointId: test_raw_filter

     - Configure the threshold rules for the raw data: the threshold values for the input point is (0, 90.00), and the output point is *test_raw_filter*.
   * - 4
     - Window Aggregator
     - + Aggregation Window Type: Fixed Window Aggregator
       + Fixed Window Unit: minute
       + Fixed Window Size: 2
       + Latency (Minute): 0
       + Model::PointIn: testModel::test_raw_filter
       + Aggregator Policy: avg
       + PointOut: test_raw_dq

     - Configure the window aggregation rules: the window type is fixed window, the window size is set as 2 min, the latency is set as 0, and the aggregation algorithm is set as avg.
   * - 5
     - Data Distination
     - + Topic: MEASURE_POINT_INTERNAL     
       + Data Format: JSON

     - Configure the data output.


<br />

The figure below shows the configuration of the stream data processing job:

.. image:: ../media/streamsets_job.png

### Step 2: Save, publish, and start the stream processing job

After configuring the stream data processing job, click the Start icon |icon_start| to start the job. To view the job running status,  return to the job list page.

### Step 3: View the data quality report
Go to the **EnOS Management Console > Data Quality** module and enter the query conditions (Model: *testModel*; Measuring points: *test_raw_filter* and *test_raw_dq*) to query the data quality report of the measurement points. For details of viewing the data quality report, see [Viewing the Data Quality Report](../howto/quality/managing_data_quality).


.. |icon_start| image:: ../media/icon_start.png
