# Point Selector

This stage selects the points that are required for stream data processing from the Kafka topics of the organization unit. The functions of this stage include:

- Selecting points based the specified model IDs and point IDs.
- Supporting multiple entries of model IDs and point IDs. If the input data matches with the specified model IDs and point IDs, the data record will be the output of the stage.
- If the input data does not match with the specified model IDs and point IDs, the stage will not have output.

<br />

This stage does not support streaming lineage.


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
     - Specify the data input point to be processed by the pipeline, using the format {modelId}::{pointId}.


## Output Results

The output results of this stage are the streaming records that are filtered by `pointId` and `modelIdPath`.


### Output Example

.. image:: media/point_selector_result.png

<!--end-->
