# Developing with StreamSets Operators
EnOS Stream Analysis provides a set of underlying packaged StreamSets operators for developers to develop customized stream data processing jobs to meet the requirements of various business scenarios.

## Overview

StreamSets provides a user-friendly UI for designing data processing jobs (pipelines) by drag-and-drop operations. You can quickly configure pipelines by adding operators (stages) to the pipeline, thus completing data ingestion, filtering, processing, and storage tasks without programming.

A data processing pipeline usually consists of multiple stages that are connected by arrows, defining the stream of data. Data flows and transforms sequentially through the pipeline. Each stage represents a read-and-write or processing operation to the data. This kind of process forms a stream data processing job. A pipeline can include the following stages:

- **Origin**

  Stage for specifying the data source and transforming data to the stages that follows, such as the Kafka Consumer stage.

- **Processor**

  Stage for data conversion,  which can normalize or transform the input data (such as data filtering, transforming, calculation, etc.).

- **Destination**

  Stage for storing the processed data in the target storage or sending data for further processing.

## Designing a Pipeline

EnOS provides a template for designing StreamSets pipelines. You can import the pipeline configuration template the design a data processing pipeline quickly:

1. [Download the StreamSets pipeline configuration template](../../_static/streamsets_pipeline_demo.json) and save the `streamsets_pipeline_demo.json` file to a local directory.

2. Log in EnOS Console, select **Stream Data Processing > StreamSets**, click the triangle beside the **Create New Pipeline** button, and select **Import Pipeline**.

3. On the **Import Pipeline** window, enter a pipeline title and optional description, click **Browse ...**, navigate and select the configuration template file, and click **Import**.

   .. image:: ../../media/streamsets_import_pipeline.png

4. Set the yarn queue for the new pipeline. Click the **Cluster** tab, set the value of the `spark.yarn.queue` field as `root.streaming_{orgId}`, in which `orgId`  is the organization ID (can be retrieved on the **IAM > Organization Profile** page on EnOS Console).

   .. image:: ../../media/streamsets_yarn_queue.png

5. Set the Kafka Consumer Group. Select the **Data Source** Stage, click the **Kafka** tab, and set the value of the **Consumer Group** parameter (which must be unique within the organization). 

   .. image:: ../../media/streamsets_kafka_consumer.png

6. Select a stage you want to use (like the Point Selector) from the **Stage Library** in the upper right corner of the page to add it to the pipeline canvas.

   .. image:: ../../media/streamsets_stage_library.png

7. Connect the origin stage to the new stage to add it to the pipeline. Select the new stage and complete the parameter configuration.

   .. image:: ../../media/streamsets_add_stage.png

8. Repeat steps 6 and 7 to add more stages to the pipeline and complete the parameter configuration of the stages.

9. Click the **Validate** icon in the tool bar to check the parameter configuration of the stages. If the validation fails, update the configuration accordingly.

   .. image:: ../../media/streamsets_validation.png

For more information about designing StreamSets pipelines, see [StreamSets User Guide](https://streamsets.com/documentation/controlhub/2.0.9/help/controlhub/UserGuide/PipelineDesign/PipelineDesign.html).

## Previewing and Running the Pipeline

If the validation is successful, you can preview and run the pipeline.

1. Click the **Preview** icon in the tool bar, enter the preview configuration, and click **Run Preview**.

2. Select any stage in the pipeline to check the input data and output data of the stage.

   .. image:: ../../media/streamsets_preview.png

3. If the preview runs correctly as designed, stop the preview, and click the **Start** icon in the tool bar to start running the pipeline.

4. When the pipeline is running, you can check the data processing result in the **Monitoring** section.

   .. image:: ../../media/streamsets_result.png

## StreamSets Operator Documentation

For detailed information about the function, parameter configuration, and output of the available operators, see [StreamSets Operator Reference](../../reference/streamsets/index).