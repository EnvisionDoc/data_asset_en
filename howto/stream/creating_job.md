# Creating a Stream Processing Job

<br />

You can use the data processing templates that are provided by the EnOS Stream Processing Service to quickly create stream processing jobs. Stream processing jobs can be created from scratch or by importing an existing configuration file.

<br />

Follow the steps below to create a stream processing job.

1. Log in to the **EnOS Management Console** and click **Stream Processing > Stream Development**.

2. Click the + icon above the list of stream processing jobs to open the **New Stream** window.

3. Select *New* for the method of creating the stream processing job.

4. From the **Message Channel** drop-down list, select the source of data to be processed.

   - If the data is ingested from connected devices, select *Real-Time*.
   - If the data is integrated through the offline message channel, select *Offline*.

5. Enter the name and description of the stream processing job.

6. Select a template from the **Template** drop-down list and select a **Version** for the template.

7. Click **OK** to create the stream processing job with the basic settings above. You can then continue on to configure the data processing policy.

.. image:: ../../media/create_stream.png
   :width: 400px

<!--end-->

<!--end-->
