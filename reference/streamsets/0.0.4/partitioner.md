# Partitioner

This stage partitions the records of each batch by the specified conditions and is usually used for joint operations among different points of the same device, or operations among points of different devices. The functions of this stage include:

- Supporting customized partitioning conditions.
- Supporting path expressions in customized partitioning conditions. For example, `/assetId` indicates partitioning by the value of the `assetId` field in each record.

<br />

This stage does not support streaming lineage.

## Configuration

The configuration tabs for this stage are **General** and **Partitioner**. 

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


### Partitioner

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Parallelism (Standalone Mode Only)
     - Yes
     - Specify the number of partitions to create per batch of records in Standalone mode.   
   * - Application Name (Standalone Mode Only)
     - Yes
     - The name of the application that runs this stage in Standalone mode (SDC Spark App by default).
   * - Init Method Arguments
     - Yes
     - Specify the record fields used for creating partitions. For example, specifying /assetId means assigning records with the same assetId to the same partition.


## Output Results

The output results of this stage are the records after partitioning.


### Output Example

.. image:: media/partitioner_result.png

<!--end-->
