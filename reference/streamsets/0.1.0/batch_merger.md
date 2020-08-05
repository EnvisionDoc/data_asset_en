# Batch Merger

This stage generates a group tag for each record in the current batch based on the specified condition. The records are then merged with the same tag and output in a single record. The function of this stage includes:

- Supporting 2 methods for generating group keys: by record field value or EL expression.


## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, and **Group Key**. 

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
   * - Output Point
     - Yes
     - Specify the output point of the records, using the format {modelId}::{pointId}.


### Group Key

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Key Generate Method
     - Yes
     - Select the method for generating group tags. The options are **By Record Field Value** and **By EL Expression**.
   * - Fields
     - No
     - When **By Record Field Value** is selected, select or specify the field name.
   * - EL Expression
     - No
     - When **By EL Expression** is selected, type the expression for generating the group keys.


## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - crossBatch
     - Map
     - The collection of records with the same group key.


### Output Example

.. image:: media/cross_batch_merger.png

<!--end-->
