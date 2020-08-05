# Record Restorer

This stage parses the data records that pass through this stage, filter records that match with the input data of the current batch, retrieve the cached data from Redis, and output the data records after renaming.

This stage has a dependency on the Record Capturer stage.

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
     - Specify the input point that triggers the reading of the cached data, using the format {modelId}::{pointId}.
   * - Restore Point
     - Yes
     - Specify the point data to be retrieved from the cache, using the format {modelId}::{pointId}.
   * - Output Point
     - Yes
     - Specify the output point used for renaming the cached data, using the format {modelId}::{pointId}.


## Output Results

The data records of the specified device and point will be retrieved from the cache and output after renaming.

### Output Example

.. image:: media/record_restorer_result.png

<!--end-->
