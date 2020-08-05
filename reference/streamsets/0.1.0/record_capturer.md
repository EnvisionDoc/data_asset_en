# Record Capturer

This stage captures the data that passes through this stage and store the data in Redis in the `key:field:value` format. The calculation logic of this stage is as follows:

- The format of the Redis key is `pipelineId::commonRedisStage::assetId`, in which `commonRedisStage` is a fixed field.
- This stage cannot guarantee idempotence of the calculation results due to failure retries caused by any reasons, such as cluster node exceptions.


## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, and **CacheConfig**.

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

### CacheConfig

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Cache Type
     - Yes
     - Select the storage type for cache data. Options are Redis and Local storage.

       + Redis: The advantage is that the cached data will not be lost after the stream processing job is paused, restarted, or retried. The disadvantage is that the data processing speed is slow.
       + Local: The advantage is that the data processing speed is fast. The disadvantage is that the cached data will be lost after the stream processing job is paused, restarted, or retried.

## Output Results

The records passing through the stage will be stored in Redis.

### Output Example

.. image:: media/record_capturer_result.png

<!--end-->
