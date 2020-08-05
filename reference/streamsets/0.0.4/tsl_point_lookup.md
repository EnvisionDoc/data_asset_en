# TSL Point Lookup

This stage queries the tags of a specified asset measurement point. The functions of this stage include:

- Supporting the querying of the information of a point related to the input record.
- Supporting the querying of the specified tags.
- Supporting the querying of the customized pointId, which must belong to the same device with the input point.
- Attaching queried results in the `/attr/tslPointLookup` field.

## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, and **Criteria**. 

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
     - The measurement point attribute data that is attached to each record. Specify the input points that hold the measurement point attribute data, and the output points that receive the queried results.
   * - Input Point
     - Yes
     - Specify the input point that holds the measurement point attribute data, using the format {modelId}::{pointId}.
   * - Output Point
     - Yes
     - Specify the output point that receives the queried results, using the format {modelId}::{pointId}.

### Criteria

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Tag
     - No
     - Specify whether to query the measurement point attribute data by tags.
   * - Extra
     - No
     - Specify whether to query the measurement point attribute data by other information, such as name, desc, accessMode, dataType, createTime, priority, unit, signalType, and hasQuality.

## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields as follows:

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - /attr/tslPointLookup
     - Point
     - The point attribute information object.
   * - tags
     - Map
     - The list of measuring point tags.

### Output Example

.. image:: media/tsl_point_lookup_result.png

<!--end-->
