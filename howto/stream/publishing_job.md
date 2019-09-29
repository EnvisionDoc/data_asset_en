# Publishing the Stream Processing Job

After the configuration of stream data processing policy is completed, you can make other configuration to the stream processing job, such as saving the data processing policy, setting alarms, reverting the configuration to the online version, and exporting the configuration.

- **Save**: After the stream processing configuration is completed, click **Save** to save the configuration, so that the stream can be published online.
- **Export**: If you want to reuse the stream processing configuration, click **Export** to export the configuration file to a local directory. When creating other jobs, you can import the saved configuration file for reference.
- **Revert to Online Version**: When you are in the progress of editing the stream processing configuration of an online job and get unsatisfied with the changes, you can revert the configuration to the online version with one click.
- **Alarm Setting**: For each stream processing job, an alarm can be set to report errors through email or SMS. When errors are reported for running jobs, the owner of the stream processing job will receive notification.
- **Release**: After the stream processing job configuration is saved, click **Release** to publish the job online.

.. note:: Before releasing the job online, ensure that the job does not have an online running version. Otherwise, pause the running job on the **Stream Operation** page and then release the updated job online.

.. image:: ../../media/config_stream.png

After the stream processing job is published online, you can start it on the **Stream Operation** page. Before that, ensure that computing resources have been allocated for your organization. To request computing resources, see [Managing Resources](/docs/enos/en/latest/resourcemanagement/getstarted.html).

## Next Steps

[Monitoring the Stream Processing Job](monitoring_job)
