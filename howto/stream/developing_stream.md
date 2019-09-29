# Developing a Stream Processing Job

The general process of developing a stream processing job is as follows:

1. Create a stream processing job

2. Configure the stream processing job with templates

3. Save and publish the stream processing job

4. Run and monitoring the status of the stream processing job

## Creating a Stream Processing Job

You can quickly create a stream processing job with the templates provided by EnOS Stream Processing Engine or by importing the configuration file of an existing job. Take the following steps to create a stream processing job.

1. Log in EnOS Console and click **Stream Data Processing** > **Stream Development**.

2. Click the **+** icon above the stream list to open the **New Stream** window.

3. From the **Message Channel** drop-down list, select the type of stream data to be processed:

   - **Real-Time**: For data ingested and uploaded from connected devices.
   - **Offline**: For data integrated from the "Message Integration" module.

4. Enter the name and description of the stream processing job.

5. From the **Template** drop-down list, select a stream processing template.

6. Click **OK** to complete creating the stream processing job and open the data processing policy configuration page.

.. image:: ../media/create_stream.png

## Configuring Stream Processing Policy

EnOS Stream Processing System provides the following templates for configuring stream data processing policies quickly:

- Time Window Aggregation template: Supporting aggregation of AI type data of a single measuring point and assigning the processed data to another measuring point on the same device. For details, see [Time Window Aggregation Template](../learn/ai_template_overview).  
- Multi-Point Merging template: Supporting aggregation of multiple measuring points of a device and assigning the processed data to another measuring point on the same device, by writing customized calculation expressions. For details, see [Multi-Point Merging Template](../learn/multi_point_overview).
- Electric Power Calculation template: Supporting calculating electric power data uploaded from electric meters with specific calculation method and assigning the total electric power data or detailed data in a time interval to measuring points in the same model. For details, see [Electric Power Calculation Template](../learn/pi_template_overview).

## Saving and Publishing the Stream Processing Job

After the configuration of stream data processing policy is completed, you can make other configuration to the stream processing job, such as saving the data processing policy, setting alarms, reverting the configuration to the online version, and exporting the configuration.

- **Save**: After the stream processing configuration is completed, click **Save** to save the configuration, so that the stream can be published online.

- **Export**: If you want to reuse the stream processing configuration, click **Export** to export the configuration file to a local directory. When creating other jobs, you can import the saved configuration file for reference.

- **Revert to Online Version**: When you are in the progress of editing the stream processing configuration of an online job and get unsatisfied with the changes, you can revert the configuration to the online version with one click.

- **Alarm Setting**: For each stream processing job, an alarm can be set to report errors through email or SMS. When errors are reported for running jobs, the owner of the stream processing job will receive notification.

- **Release**: After the stream processing job configuration is saved, click **Release** to release the job online.

  .. note:: Before releasing the job online, ensure that the job does not have an online running version. Otherwise, pause the running job on the **Stream Operation** page and then release the updated job online.

.. image:: ../media/config_stream.png

After the stream processing job is published online, you can start it on the **Stream Operation** page. Before that, ensure that computing resources have been allocated for your organization. To request computing resources, see [Requesting Resources](/docs/enos/en/latest/resourcemanagement/getstarted.html).
