# Sliding Time Window Aggregator

This stage aggregates the data of a single point by the sliding time window. The settings for this stage are as per the below.

- Window type: Sliding window.
- Supported aggregators: max/min/avg/count/sum/first/last.
- This stage cannot guarantee idempotence of the calculation results due to failure retries caused by any reasons, such as cluster node exceptions.

## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, **ExtraConfig**, and **CacheConfig**.

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
     - Specify the duration for the fixed time window, which is equal to the step length of the sliding window.
   * - Fixed Window Unit
     - Yes
     - Select the unit for the fixed time window.
   * - Sliding Window Size
     - Yes
     - Specify the step length of the sliding window.
   * - Sliding Window Unit
     - Yes
     - Select the unit for the sliding window.
   * - Aggregator Policy
     - Yes
     - Select the aggregator for data aggregation: max/min/avg/count/sum/first/last.
   * - Output Point
     - Yes
     - Specify the output point of thr records, using the format {modelId}::{pointId}.

### ### ExtraConfig

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Output Data Type
     - Yes
     - Select the output data type. Options are Double and From TSL Model Service.

       + Double: You can select this option if the output points are all for intermediate calculation results (the output points are not defined on the model), or the data type of all the output points is Double.
       + From TSL Model Service: You must select this option if the output points are defined on the model and the data type of the points is not Double. Otherwise, the output data cannot be stored in TSDB correctly.

### CacheConfig

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Cache Type
     - Yes
     - Select the storage type for cache data. Options are Redis and Local storage.

       + Redis: The advantage is that the cached data will not be lost after the stream processing job is paused, restarted, or retried. The disadvantage is that the data processing speed is slow.
       + Local: The advantage is that the data processing speed is fast. The disadvantage is that the cached data will be lost after the stream processing job is paused, restarted, or retried.

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
     - The output mode, which is the final output.
   * - calType
     - String
     - The selected aggregator: max/min/avg/count/sum/first/last.
   * - calDetail
     - Map
     - The calculation details. For example, when calType=avg, output the sum and count value of `value` and `lastValue`.


### Output Example

.. image:: media/sliding_window_aggregator.png

<!--end-->
