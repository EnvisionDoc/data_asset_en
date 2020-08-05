# Dev Raw Data Source

This stage generates raw data based on the user-provided data, which can be used for debugging only.

<br />

This is a native StreamSets stage. For more information, see [Development Stages](https://streamsets.com/documentation/datacollector/latest/help/datacollector/UserGuide/Pipeline_Design/DevStages.html).


## Configuration

Before using this stage, set the Execution Mode of the pipeline as `Standalone`.

.. image:: media/dev_raw_data_source_config.png

<br />

The configuration tabs for this stage are **General**, **Raw Data**, and **Data Format**. 

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
   * - On Record Error
     - Yes
     - The processing method for error data.

       + Discard: Error data will be discarded and ignored
       + Send to Error: Error messages will be reported
       + Stop Pipeline: The pipeline will be stopped

### Raw Data

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Raw Data
     - Yes
     - The raw data, for example, `{"orgId":"xxx","modelId":"Model","modelIdPath":"/rootModel/Model","assetId":"qXupozjG","pointId":"Point_A","time":1567292293000,"value":1.2,"quality":0,"attr":{}}`
   * - Stop After First Batch
     - No
     - Specify whether to stop after generating the first batch of data records.

### Data Format

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Data Format
     - Yes
     - Select the format of the generated data. Options include JSON, Log, Text, XML, etc. It is recommended to select JSON.
   * - Compression Format
     - Yes
     - Select the data compression format. It is recommended to select None.
   * - Other fields
     - No
     - Complete the configuration based on the raw data provided and selected data format.


## Output Results

The output results of this stage are based on the raw data provided and selected data format.

### Output Example

.. image:: media/dev_raw_data_source_result.png

<!--end-->
