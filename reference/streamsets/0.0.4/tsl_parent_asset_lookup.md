# TSL Parent Asset Lookup

This stage queries the parent node of a specified asset on an asset tree. The functions of this stage include:

- Specifying the asset tree by asset tree tags.
- Querying the parent node of the asset related to the input point.
- Querying only 1 level of parent node on the asset tree by default.
- Support the querying of the parent node of a specified node on the asset tree.
- Attaching queried results in the `/attr/tslParentLookup` field.


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
     - The parent asset metadata that is attached to each record. Specify the input points that hold the parent asset metadata, and the output points that receive the queried results.
   * - Input Point
     - Yes
     - Specify the input point that holds the parent asset metadata, using the format {modelId}::{pointId}.
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
   * - Tree Tag
     - Yes
     - Specify the tag of the asset tree, using the format {tag key}::{tag value}.
   * - Attribute
     - No
     - Specify whether to query the parent asset metadata by the asset attribute keys.
   * - Tag
     - No
     - Specify whether to query the parent asset metadata by the asset tags.
   * - Extra
     - No
     - Specify whether to query the parent asset metadata by other information, such as othe OU, modelId, modelIdPath, tslInstanceName, tslInstanceDesc, label, timezone, and extraInfo.

## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - /attr/tslParentLookup
     - List<Parent>
     - The parent asset metadata object.
   * - List index
     - Int
     - The index of the parent asset.
   * - treeId
     - String
     - The ID of the asset tree to which the parent asset is bound.
   * - assetId
     - String
     - The asset ID of the parent asset.
   * - attributes
     - List<attributeId>
     - The list of parent asset attributes.
   * - tags
     - List<tagId>
     - The list of parent asset tags.
   * - timezone
     - String
     - The timezone of the parent asset.

### Output Example

.. image:: media/tsl_parent_asset_lookup_result.png

<!--end-->
