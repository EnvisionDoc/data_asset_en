# Late Point Tagger

This stage supports the recognizing of late data and the tagging of late data points for generating data quality reports. The specific logic is as follows:

- Use the `timestamp` field as the standard to filter late records. If the `timestamp` of a record is "later" than that of the latest record, the record will be recognized as late data.
- The judging logic applies to records of the same point and same device.
- For the first arriving record of a new point and new device, it will be recognized as "not late". Its timestamp will be used to judge records arriving after it.

<br />

This stage supports streaming lineage.


## Configuration

The configuration tabs for this stage are **General**, **Basic**, and **Input/Output**. 

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
     - Specify the input point of the records, using the format {modelId}::{pointId}. For the same configuration row, the modelId must be the same, and the input point and the output point must be different.
   * - Output Point
     - Yes
     - Specify the output point of the records, using the format {modelId}::{pointId}. For the same configuration row, the modelId must be the same, and the input point and the output point must be different.


## Output Results

Records that are processed by this stage will be appended with the data quality tag (for generating data quality reports). Values of the data quality tags indicate whether the data records are arriving late.

### Output Example

**Normal point**

.. image:: media/late_point_filter_result_1.png

**Late point**

.. image:: media/late_point_filter_result_2.png

<!--end-->
