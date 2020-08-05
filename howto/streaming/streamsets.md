# Developing with StreamSets Calculators

<br />

The EnOS Stream Processing Service provides a set of underlying packaged StreamSets calculators for developers to develop customized stream data processing jobs to meet the requirements of complex business scenarios.

## Overview

EnOS Stream Processing Service provides a user-friendly drag-and-drop UI for designing data processing jobs (pipelines). You can quickly configure pipelines by adding calculators (stages) to the pipeline, thus completing data ingestion, filtering, processing, and storage tasks without any programming.

<br />

A data processing pipeline usually consists of multiple stages that are connected by arrows that define the data stream, though which the data sequentially flows. Each stage represents a read-and-write or processing operation to the data. This kind of process forms a stream data processing job. A pipeline can include the following stages.

- **Origin**

  The stage that specifies the data source and passes the output data to later stages, such as the Kafka Consumer stage.

- **Processor**

  The stage for data conversion, where the input data is normalized or changed (such as data filtering, transforming, calculation, etc.).

- **Destination**

  The stage for storing the processed data in the target storage or sending data for further processing.


## Designing a Pipeline

<br />

**Prerequisites**

The EnOS Stream Processing Service provides multiple versions of StreamSets calculator libraries. Before designing stream data processing jobs, you need to install the needed version of calculator library. For more information, see [Installing Calculator Libraries or Templates](installing_lib).

<br />

**Develop a Stream Data Processing Job with StreamSets Calculators**

1. Log in to the **EnOS Management Console**, select **Stream Processing > Stream Development**, and click the **+** icon above the list of stream processing jobs.

2. On the **New Stream** window, select **New** to create the stream processing job. You can also choose to import a configuration file to create the job quickly.

3. Enter the name and description of the stream processing job.

4. From the **Template** drop-down list, select **Origin Pipeline**.

5. From the **Operator Version** drop-down list, select the installed StreamSets calculator library version.

6. For **Message Channel**, select the source of data to be processed:

   - If the data is ingested from connected devices, select *Real-Time*.
   - If the data is integrated through the offline message channel, select *Offline*.


7. Click **OK** to create the stream processing job with the basic settings above.

   .. image:: ../../media/creating_streamsets_pipeline.png
      :width: 400px


## Designing the Stream Processing Pipeline

Follow the steps below to design the stream processing pipeline with stages.

1. On the pipeline designing canvas, select a stage you want to use (like the **Point Selector** stage) from the **Stage Library** in the upper right corner of the page to add it to the canvas.

   .. image:: ../../media/streamsets_stage_library.png

   <br />

2. Delete the arrow connecting the **Kafka DataSource** and **Kafka Producer** stages and connect the Data Source stage to the new stage by clicking the output point of the Data Source stage and dragging it to the input point of the new stage. Do the same to connect the new stage to the Producer stage to complete adding the new stage to the pipeline. Click on the new stage and complete the parameter configuration.

   .. image:: ../../media/streamsets_add_stage.png

   <br />

3. Repeat steps 1 and 2 to add more stages to the pipeline and complete the parameter configuration of the added stages.

4. Click **Save** in the tool bar to save the configuration of the pipeline.

5. Click the **Validate** icon |icon_validate| in the tool bar to check the parameter configuration of the stages. If the validation fails, update the configuration accordingly.

   .. image:: ../../media/streamsets_validation.png

<br />

For more information about designing StreamSets pipelines, see [StreamSets User Guide](https://streamsets.com/documentation/controlhub/latest/help/controlhub/UserGuide/GettingStarted/GettingStarted_title.html).


## Publishing and Running the Pipeline

If the validation is successful, you can publish the pipelien online and start it.

1. Click **Release** in the tool bar to publish the pipeline.

2. Open the **Stream Processing > Stream Operation** page, view the published pipeline, whose status is *PUBLISHED* by default.

3. Complete the running resource configuration and alarm settings for the pipeline, ensure that the required system pipelines are running, and click the **Start** icon |icon_start| to start running the pipeline.

<br />

For more information about pipeline operations, see [Maintaining Stream Processing Jobs](monitoring_job).


## StreamSets Operator Documentation

For detailed information about the function, parameter configuration, and output of the available StreamSets calculators, see the [StreamSets Calculator Documentation](../../reference/streamsets/index).


## Tutorial

To learn how to develop a stream data processing pipeline for a more complex business scenario, see [Developing with StreamSets Operators](../../tutorial/developing_with_streamsets_operators/index).


.. |icon_start| image:: ../../media/start_icon.png
.. |icon_validate| image:: ../../media/icon_validate.png

<!--end-->
