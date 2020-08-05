# Managing Data Archiving Jobs

<br />

When a data archiving job is configured and submitted, the system will start archiving data immediately as per the configuration. In the list of data archiving jobs, you can view the running status of all the jobs, set alarms for the jobs, edit the job configuration, stop a job, and delete a job.

## Setting Alarms

In case of any exceptions like failure to run an archiving job or data loss during data archiving, the owner of the data archiving job need to receive an alarm through email or SMS. You can set alarms for a data archiving job by the following steps:

1. On the **Data Archiving** page, find the data archiving job from the job list.

2. From the **Operations** column, select **... > Alarm Setting** to open the **Alarm Setting** window.

3. Select the **Receiver** of alarms and the **Mode** to send the alarms (Email or SMS).

4. Click **OK** to save the alarm settings.

   .. image:: ../../media/archiving_job_alarm.png

<!--

## Viewing Logs

You can view the running logs of a running data archiving job.

1. On the **Data Archiving** page, find the submitted data archiving policy in the list of policies.
2. Click **Operations > View Log** to open and view the log file.
3. Click **Download Logs** to download and save the log file of the data archiving job.

The log file contains the configuration of the data archiving policy, the archiving job status, the archiving job progress, the number of archived files, and the number of files synchronized to the target storage system.

-->

## Editing Job Configuration

If required by business needs, you can edit and update the configuration of any submitted data archiving job.

1. On the **Data Archiving** page, find the data archiving job from the job list.

2. Click the **Edit** icon in the **Operations** column to open the configuration page of the data archiving job.

3. Update the data archiving job configuration as per business needs (such as the basic information, storage resource and path, archive file name and size, archive cycle, and the data configuration).

4. Click **OK** to submit the updated configuration.

<br />

The updated data archiving job will take effect immediately once it is submitted. Any data archiving job that is not completed in the current archiving cycle will restart immediately as per the newly-submitted configuration. Archived files will not be affected. Data of the newly added models will be archived immediately.

## Stopping a Data Archiving Job

You can stop a data archiving job whose data source is offline message channel. Click the **Stop** icon in the **Operations** column to stop a running job.

<br />

If the stopped job is restarted, the job will not resume data archiving from the point when it is stopped. A new data archiving job will be running.  

<br />

Data archiving jobs whose data source is real-time message channel or real-time alert record cannot be stopped manually. To stop archiving data, you can delete the corresponding data archiving job. Archived files will not be affected when the job is deleted.

## Deleting a Data Archiving Job

You can delete a data archiving job with the following steps.

1. On the **Data Archiving** page, find the data archiving job from the job list.

2. From the **Operations** column, select **... > Delete** and confirm to delete the job.

<br />

Once a data archiving job is deleted, the current archiving job will stop immediately. Data been synchronized to the storage system will not be affected. The archived files cached in the platform will be deleted directly and will not be synchronized to the storage system. Archived files that are in the process of synchronization will be synchronized continuously until the synchronization is completed.
