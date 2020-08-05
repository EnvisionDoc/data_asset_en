# Last Changed Record Appender

This stage caches the latest data of each point and appends the latest data to each record. 

<br />

For a single point of a single device:

- If there is no existing record of the point 
    + Cache the data of the point
    + Append the cached data to the `/attr/lastChangedRecordAppender` field of the record
- If there is an existing record of the point
    + Append the current cached data to the `/attr/lastChangedRecordAppender` field of the record
    + Compare the data with the cached data. If there are differences, refresh the cached data with the arrived data.


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
   * - Input/Output
     - Yes
     - The last changed data is attached to each record. Specify the input points that hold the last changed data, and the output points that receive the output results.
   * - Input Point
     - Yes
     - Specify the input point that holds the last changed data, using the format {modelId}::{pointId}.
   * - Output Point
     - Yes
     - Specify the output point that receives the output results, using the format {modelId}::{pointId}.


## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 40 20 40

   * - Name
     - Data Type
     - Description
   * - lastChangedRecordAppender
     - Map
     - The point attribute data object.
   * - lastChangedTs
     - Long
     - The timestamp of the last changed record.
   * - lastChangedValue
     - Object
     - The value of the last changed record.
   * - lastChangedRecord
     - Map
     - The complete information of the last changed record.


### Output Example

.. image:: media/last_changed_record_appender.png

<!--end-->
