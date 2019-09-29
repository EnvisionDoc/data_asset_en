# Monitoring the Stream Processing Job

After the stream processing job is published online, you can manage the job through various operations on the **Stream Operation** page, such as requesting computing resources, previewing the stream processing job, starting the job, pausing and stopping a running job, and checking the running status of the job.

## Requesting Computing Resources

Before starting the stream processing job, you need to check whether computing resources have been allocated for your organization. Otherwise, stream processing job cannot be started up. To request computing resources, see [Managing Resources](/docs/enos/en/latest/resourcemanagement/getstarted.html).

## Previewing the Stream Processing Job

Before starting the stream processing job, you can preview its running result with a small batch of data.

1. On the **Stream Operation** page, click the job name to view the detailed information.

2. Click the **Preview** button on the upper right corner of the page.

3. Complete the preview configuration and run the preview.

The preview will intercept and process the latest real-time data, and the processed data will not be saved in the DB. With the preview results, you can debug and tune the stream processing job. If the preview results meet the expectation, you can start the job directly.

## Maintaining Stream Processing Jobs

On the **Stream Operation** page, you can perform the following actions for stream processing jobs:

- **Start a job**: Click the **Start** icon |start_icon| in the **Operations** column of the job list to start a job. Then the job will run continuously in the streaming system.

  .. note:: To start a new stream processing job, pause one or more running jobs and start the new job with the others together. The system will reallocate resources for all the jobs.

- **Pause a job**: Click the **Pause** icon |pause_icon| in the **Operations** column of the job list to pause a running job. After the job is paused, the cached data will be reserved. When the job is started again, the computing will continue consuming data from the point when the job was paused. Note that the job cannot be paused for more than 24 hours.

- **Stop a job**: Click the **Stop** icon |stop_icon| in the **Operations** column of the job list to stop a running job. After the job is stopped, the cached data and the data consumption offset information of the job will be cleared. When the job is started again, the computing will consume data from the point when the job was stopped, but the computed data before the job was stopped is not stored.

- **View configuration**: Select **More > View** from the **Operations** column to view the stream processing configuration details.

- **Export configuration**: Select **More > Export** from the **Operations** column to download the stream processing configuration file.

- **Start/Pause multiple jobs**: Select multiple jobs and click the **Start** or **Pause** button to start multiple jobs or pause multiple running jobs together.


## Viewing Running Results

When the stream processing job is started, you can click the name of a running job to view its running status, including its running result summary and error logs.

.. |start_icon| image:: ../../media/start_icon.png

.. |pause_icon| image:: ../../media/pause_icon.png

.. |stop_icon| image:: ../../media/stop_icon.png

<!--end-->
