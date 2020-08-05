# Latest Record Merger

This stage generates group tags based on the specified expression. Multiple input points are grouped by the generated tags and output the points by groups. When the specified point arrives, an output will be triggered. The functions of this stage include:

- Supporting the input of multiple points of multiple models, and multiple input points as calculation trigger points
- Supporting the output of multiple points of multiple models. The `modelId`, `modelIdPath`, and `pointId` of the input point will be replaced with those of the output point.


## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, and **MergerConfig**. 

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
     - Specify the measurement point for record merging using the format {modelId}::{pointId}.
   * - Is Trigger
     - No
     - Specify whether to set the point as the trigger for processing.
   * - Output Point
     - Yes
     - Specify the point for receiving output results using the format {modelId}::{pointId}.

### MergerConfig

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Merged By Expression
     - Yes
     - Specify the expression for generating the tags that are used to merge the latest records.
   * - Cache Expire Time (Minute)
     - Yes
     - Specify the cache expiring time after the tags are not updated.


## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 40 20 40

   * - Name
     - Data Type
     - Description
   * - /attr/latestRecordMerger
     - Map
     - The data object after merging.
   * - mergedTag
     - String
     - The tags that are generated based on the EL expression.
   * - mergedRecords
     - List
     - The list of records after merging.


### Output Example

.. image:: media/lastest_record_merger.png

<!--end-->
