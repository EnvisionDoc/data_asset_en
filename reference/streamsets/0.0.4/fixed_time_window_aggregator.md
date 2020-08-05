# Fixed Time Window Aggregator

This stage aggregates the data of a single point by the fixed time window. The settings for this stage are as per the below.

- Window type: Tumbling window.
- Supported aggregators: max/min/avg/count/sum/first/last.
- Latency settings: Support the processing of data that arrives 0~60 minutes late.
- Early output: Support the early output of intermediate results before the time window is closed (by fixed frequency or by arriving input data).

## Configuration

The configuration tabs for this stage are **General**, **Basic**, **TriggerConfig**, and **Input/Output**. 

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
   * - Quality Filter
     - No
     - Filter the data according to the data quality. Only records that meet the quality conditions will be processed by this stage.


### TriggerConfig

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Latency (Minute)
     - Yes
     - Configure the data latency settings, allowing data to arrive 0~60 minutes late.
   * - Early Trigger
     - No
     - Specify whether to enable the early output of intermediate results before the time window is closed.
   * - Early Trigger Type
     - No
     - Select the method for the early output of intermediate results. The methods are by fixed frequency or by input point.


### Input/Output

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Input Point
     - Yes
     - Specify the input point of the records, using the format {modelId}::{pointId}.
   * - Fixed Window Size
     - Yes
     - Specify the duration for the fixed time window.
   * - Fixed Window Unit
     - Yes
     - Select the unit for the fixed time window.
   * - Aggregator Policy
     - Yes
     - Select the aggregator for data aggregation: max/min/avg/count/sum/first/last.
   * - Output Point
     - Yes
     - Specify the output point of the records, using the format {modelId}::{pointId}.


## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - lastOutput
     - Integer/Double/Float
     - The last output of the point (NaN for no output).
   * - calMode
     - String
     - Output mode:

       + final: The final output.
       + onTime: When **On-time Trigger** is set, output the results when the time window is closed.
       + early: When **Early Trigger** is set, output intermediate results before the time window is closed.

   * - calType
     - String
     - The selected aggregator: max/min/avg/count/sum/first/last.
   * - calDetail
     - Map
     - The calculation details. For example, when calType=avg, output the sum and count value of `value` and `lastValue`.


### Output Example

.. image:: media/fixed_window_aggregator.png

<!--end-->
