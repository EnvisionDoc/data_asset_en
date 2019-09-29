# Configuring Data Archiving Jobs
EnOS Data Connector supports archiving and storing the data from both the real-time and offline message  channels and provides flexible storage configurations to reduce your data storage costs.
## Creating a Data Archiving Job
For archiving and storing data, you need to create data archiving jobs for asset models.

1. Log in EnOS console, and select **Common Resource > Data Connector**.
2. Click **New Job**, select the message channel for the data to be archived, enter a name and description for the data archiving job.
3. Click **OK** to complete the basic setting and open the detailed configuration page of the data archiving job.

.. note:: At most 5 data archiving jobs can be created for an organization.

### Basic Information

Edit the basic information of the data archiving job if needed:

1. **Name**: Name of the data archiving job, where Chinese characters, upper cases and lower cases, numbers, underline are supported, with a length limit of 50 characters.
2. **Description**: Description of the data archiving jobs, with a length limit of 100 characters.

### Storage Configuration

Complete the data storage configuration, including configuring the storage resource, setting properties of the archived file, etc.

1. Select **Resource Type** and specify the target storage system (BLOB or HDFS) for synchronizing the archived files.
2. From the **Storage Resource** drop-down list, select the data source that has been registered through [Data Connection](/docs/offline-data/en/2.0.9/data_source/index.html) or the HDFS storage that has been requested through [Resource Management](/docs/enos/en/2.0.9/resourcemanagement/overview.html).
3. Input the **Storage Path** where the archive files are located in the storage system and select the time partition format for the storage path root directory. The path must start and end with "/". For detailed information about time partition format, see [Storage Path Partition Parameters](../../reference/archive_storage#path).
4. Select whether to generate the path by event time or by system time. For detailed description about how to generate directory by different time, see [Data Archiving Logic](../../reference/archive_storage#logic).
5. Input the **File Name** of the archived file, where upper cases, lower cases, numbers, and hyphens are supported, with a length limit of 50 characters. Once a file is generated, the system will append a time stamp suffix "_UTC" after the file name. When "Generate path by event time" is selected, the time stamp suffix is UTC+0 corresponding to the data event time; when "Generate path by system time" is selected, the time stamp suffix is UTC+0 corresponding to the system time.
6. Select **File Type**, where only TEXTFILE format (.csv) is supported currently.
7. Select the **Encoding** for archived file, where the default format is UTF-8.
8. Select **Column Delimiter**, where the default delimiter is comma.
9. Select the **Compression** format for the archived file, where the default setting is "not compressed".
10. Select the **File Size** for the archived file, that is, the file size limit before compression. If the size of a file exceeds the upper limit, the system will slice it for storage. The sliced files will be named in the form of  `filename_UTC_n`, where `n` is a 6-digit random string.

.. note:: Once the data archiving job is submitted, the file type, encoding format, column delimiter, and compression format cannot be modified.

### Archive Configuration

Select the **Archive Cycle** for the data archiving job. Currently, data archiving by every 1 hour is supported. If the archived data falls in the same archiving cycle, the data will be saved in 1 file and sliced by the specified file size.

<!--

It is suggested to select a longer archiving cycle, which is helpful to reduce the number of small files due to data latency. Different archiving cycles mean different scheduled starting time of the data archiving job as well as different data processing time range. The archived data range for each archiving cycle refers to the data generated between "the scheduled starting time for the previous archiving cycle" to "the scheduled starting time for the current archiving cycle". The archiving cycle cannot be modified once the data archiving policy is submitted.

For the scheduled starting time and archived data time range for each archiving cycle, see [Archiving Cycle Configuration](../../reference/archive_storage#cycle).

-->

### Data Configuration

Select the **Model** to which the data to be archived belongs.

After completing the above configuration, click **OK** to submit the data archiving job. The job configuration will take effect immediately once it is submitted.

When the data archiving job is submitted, the system starts reading data from the specified message channel. If the current data archiving job is not completed in the current archiving cycle, it will restart immediately per the newly-submitted configuration. Archived files will not be impacted. Data of the added models will also be archived immediately when the arching job is submitted.

For more information about how archived files are generated, see [Generation of Archived Files](../../reference/archive_storage#file).

<!--end-->
