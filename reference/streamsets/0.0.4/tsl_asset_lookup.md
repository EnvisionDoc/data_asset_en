# TSL Asset Lookup

This stage queries the asset metadata of specified devices, including attributes, tags, and timezone information. The functions of this stage include:

- Looking up asset metadata from the output record of the upstream stage by default.
- Querying the asset metadata of a specified device and writing the queried data into a record that meets the input conditions.
- Querying asset metadata by the specified criteria like attributes and tags.
- Attaching queried results in the `/attr/tslAssetLookup` field.


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
     - The asset metadata that is attached to each record. Specify the input points that hold the asset metadata, and the output points that receive the queried results.
   * - Input Point
     - Yes
     - Specify the input point that holds the asset metadata, using the format {modelId}::{pointId}.
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
   * - Attribute
     - No
     - Specify whether to query the asset metadata by the asset attribute keys.
   * - Tag
     - No
     - Specify whether to query the asset metadata by the asset tags.
   * - Extra
     - No
     - Specify whether to query the asset metadata by other information, such as the OU, modelId, modelIdPath, tslInstanceName, tslInstanceDesc, label, timezone, and extraInfo.

## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - /attr/tslAssetLookup
     - Asset
     - The asset metadata object.
   * - Asset.attributes
     - Map
     - The list of asset attributes.
   * - Asset.tags  
     - Map
     - The list of asset tags.
   * - Asset.timezone
     - String
     - The timezone of the asset.

### Output Example

.. image:: media/tsl_asset_lookup_result.png

<!--end-->
