# Publishing Stream Processing Jobs

<br />

After the configuration of the stream data processing policy is completed, you can make other configurations to the stream processing job, such as saving the data processing policy, exporting the configuration, reverting the configuration to the online version, and publishing the data processing job.

- **Save**: After the stream processing configuration is completed, click **Save** to save the configuration, so that the stream processing job can be published online.

- **Export**: If you want to reuse the stream processing configuration, click **Export** to export the configuration file to a local directory. When creating other jobs, you can import the saved configuration file as a reference.

- **Revert to Online Version**: Revert the configuration to the online version if you wish to discard any configuration changes to a job that is currently online.

- **Publish**: After the stream processing job configuration is saved, click **Release** to publish the job online. Make sure that there is no running instance of the job before publishing it online. Otherwise, pause the running job instance first on the **Stream Operation** page.

<br />

.. image:: ../../media/config_stream.png

<br />

After the stream processing job is published, you can manage it on the **Stream Operation** page.

## Next Step

[Maintaining Stream Processing Jobs](monitoring_job)
