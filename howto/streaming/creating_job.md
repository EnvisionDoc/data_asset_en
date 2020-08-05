# Creating a Stream Processing Job

<br />

You can use the data calculation templates or StreamSets calculator libraries that are provided by the EnOS Stream Processing Service to quickly create stream processing jobs. Stream processing jobs can be created from scratch or by importing an existing configuration file.


## Prerequisites

- You are able to access the Stream Processing module.
- Your OU has requested for the Stream Processing resources
- You have installed the needed data calculation templates or StreamSets calculator libraries

## Creating a Job from Scratch

1. Log in to the **EnOS Management Console** and click **Stream Processing > Stream Development**.

2. Click the **+** icon above the list of stream processing jobs to open the **New Stream** window.

3. Select *New* for the method of creating the stream processing job.

4. Enter the name and description of the stream processing job.

5. Select a template from the **Template** drop-down list and select a **Version** for the template.

6. For **Message Channel**, select the source of data to be processed:

   - If the data is ingested from connected devices, select *Real-Time*.
   - If the data is integrated through the offline message channel, select *Offline*.

7. Click **OK** to create the stream processing job with the basic settings above. You can then continue on to configure the data processing policy.

   .. image:: ../../media/create_stream.png
      :width: 400px


## Importing Job Configuration

Through importing the configuration file of an existing stream processing job, you can create another stream processing job quickly. 

1. Log in to the **EnOS Management Console** and click **Stream Processing > Stream Development**.

2. Click the + icon above the list of stream processing jobs to open the **New Stream** window.

3. Select *Import* for the method of creating the stream processing job.

4. Enter the name and description of the stream processing job.

4. Click **Select a file**, navigate and choose the configuration file of the stream processing job. The template and version information of the job will be imported automatically.

5.  In the **Message Channel** field, select the source of data to be processed:

   - If the data is ingested from connected devices, select *Real-Time*.
   - If the data is integrated through the offline message channel, select *Offline*.

6. Click **OK** to create the stream processing job and open the configuration page. You can change the stream processing configuration based on your businees needs.

   .. image:: ../../media/import_stream_config.png
      :width: 400px


<!--end-->
