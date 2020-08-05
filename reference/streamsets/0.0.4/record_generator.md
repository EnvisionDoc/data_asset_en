# Record Generator

This stage generates new records based on the specified conditions. The functions of this stage include:

- Generating required records based on the fixed calculation or querying frequency.

- Determining the dataset to be generated for the specific device and point, i.e., `Map<assetId,Set<pointId>>`, based on the filtering conditions (such as asset ID, model ID, asset tag, asset tree ID, and asset tree tag).

<br />

The triggering conditions for generating the records are based on the determined dataset:
- Get the record data from Redis based on the fixed query frequency and time interval.
- Get the record data from TSDB based on the fixed query frequency and time range.
- Simulate the record data of certain types based on the fixed calculation frequency.


## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, and **Record Generate**. 

### General

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Name
     - Yes
     - The name of the stage.
   * - Description
     - No
     - The description of the stage.
   * - Stage Library
     - Yes
     - The streaming calculator library to which the stage belongs.
   * - Required Fields
     - No
     - The fields that the data records must contain. If the specified fields are not included, the record will be filtered out.
   * - Preconditions
     - No
     - The conditions that must be satisfied by the data records. Records that do not meet the conditions will be filtered out.
   * - On Record Error
     - Yes
     - The processing method for error data.

       + Discard: Error data will be discarded and ignored
       + Send to Error: Error messages will be reported
       + Stop Pipeline: The pipeline will be stopped

### Basic

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Query Frequency
     - Yes
     - Select the frequency for generating new records.

### Input/Output

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Generate Type
     - Yes
     - Select the method to generate new records.

       + By AssetIDs：Match measurement points by asset IDs
       + By ModelIDs：Match measurement points by model IDs
       + By Asset Tags：Match measurement points by asset tags
       + By Asset Tree：Match measurement points by asset tree IDs or asset tree tags

   * - Output Asset
     - No
     - When the **By AssetIDs** method is selected, specify the asset ID. In the **Output Point** field, specify the measurement point for the generated data records, using the format {pointId}.
   * - Asset Tag
     - No
     - When the **By Asset Tags** method is selected, specify the tag key and value. In the **Output Point** field, specify the measurement point for the generated data records, using the format {modelId}::{pointId} or {pointId}.
   * - Tree Selector
     - No
     - When the **By Asset Tree** method is selected, specify the method of searching asset trees, either by asset tree IDs or by asset tree tags.
   * - Tree ID
     - No
     - Specify asset tree ID. In the **Output Point** field, specify the measurement point for the generated data records, using the format {modelId}::{pointId} or {pointId}.
   * - Tree Tag
     - No
     - Specify asset tree tag and value. In the **Output Point** field, specify the measurement point for the generated data records, using the format {modelId}::{pointId} or {pointId}.
   * - Output Point
     - Yes
     - When the **By ModelIDs** method is selected, specify the measurement point for the generated data records, using the format {modelId}::{pointId}.


### Record Generate

The methods of generating records include: Query From Redis, Query From TSDB, and Generate New Point. The configuration for each method is as follows.

#### Query From Redis

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Use LastUpdate Interval Filter
     - No
     - Select whether to get the latest asset data from Redis using a fixed time interval.
   * - LastUpdate Interval(Minutes)
     - No
     - Enter the time interval for getting the latest asset data.
   * - NotExistHandle
     - Yes
     - Select the processing method when no data is retrieved. 

       + Ignore this Point: Ignore the point data
       + Ignore and Send Error: Ignore the point data and report error

#### Query From TSDB

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Start Time
     - Yes
     - Enter the start time to query the data from TSDB, using the format `2019-08-26T00:00:00+08:00`.
   * - Time Interval
     - Yes
     - Enter the time range to query the data.
   * - End Time
     - Yes
     - Enter the end time to query the data from TSDB, using the format `2019-08-26T00:00:00+08:00`.
   * - NotExistHandle
     - Yes
     - Select the processing method when no data is retrieved. 

       + Ignore this Point: Ignore the point data
       + Ignore and Send Error: Ignore the point data and report error

#### Generate New Point

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Start Time
     - Yes
     - Enter the timestamp for the start time of the new point, using the format `2019-08-26T00:00:00+08:00`.
   * - Time Interval
     - Yes
     - Specify the time interval for generating the new point data.
   * - Value Generator
     - Yes
     - Select the method of generating new point data and the data type.

       + Random Number (Double): Randomly generate the point data.
       + Fixed Incremental as Value: Generate point data by a fixed incremental value. In the **Beginning Number** field, specify the starting value for the new point data. In the **Fixed Incremental** field, specify the fixed incremental value.
       + Random Number in Range: Randomly generate the point data within a specified value range. In the **MinMax Range** field, specify the value range. In the **Decimal Scale** field, specify the number of decimal places for the point data value.
       + Current System Time: Use the system time when the point is generated as its data value.
       + Input String as Value: Specify a string as the point data value. In the **Input field**, specify the string. In the **Data Type** menu, select the data type of the string.


## Output Results

The output results of this stage are the generated records, which include the following:

- Common fields (such as assetId, pointId, modelId, time, value)
- Stage configuration attributes, which are included in the `/attr/recordGenerator` field, described in the table below.

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - assetCfg
     - String
     - The selected method used to determine the dataset to be generated.
   * - generateBy
     - String
     - The selected method used to generate the records.
   * - queryStart/queryEnd
     - String
     - The specified start time and end time to query data from TSDB.
   * - offset
     - String
     - The count of the generated data when the record is simulated.
   * - curQueryBatch
     - String
     - The count of the record batches that triggers the generation of the simulated data.


### Output Example

#### By Tree ID + Query From Redis

.. image:: media/record_generator_result_1.png

#### By Asset ID + Query From TSDB

.. image:: media/record_generator_result_2.png

#### Generate New Point

.. image:: media/record_generator_result.png

<!--end-->
