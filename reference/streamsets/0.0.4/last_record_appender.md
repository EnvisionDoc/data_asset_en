# Last Record Appender

This stage appends the last record of the same device and same point to the `attr` field of the current record. The record to be appended must match with the specified condition. The procedure consists of the following steps.

1. Append last record to the `attr` field of the current record. If the arriving point is the first point, there is no last record.
2. Evaluate the current record with the specified condition. If the record matches with the condition, replace the current record with last record. If the condition is set to \*, always replace the current record with last record.


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
   * - Conditions
     - Yes
     - Specify the conditions for record appending. 
     
       + \* (Every record will be the last record relative to the current record) 
       + `EL Expression <https://streamsets.com/documentation/datacollector/latest/help//datacollector/UserGuide/Expression_Language/ExpressionLanguage_overview.html>`__ (the EL expression must be conditional statements, with a result of Boolean type)
   * - Output Point
     - Yes
     - Specify the output point of the records, using the format {modelId}::{pointId}. For the same configuration row, the modelId must be the same, and the input point and the output point must be different.


## Output Results

Whether the last record will be appended to the `attr` field of the current record will be based on the data attributes and the specified conditions.

### Output Example

**Without last record**

.. image:: media/last_record_result_1.png

**With last record**

.. image:: media/last_record_result_2.png

<!--end-->
