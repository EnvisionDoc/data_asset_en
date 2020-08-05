# Data Archiving Reference

## Data Archiving Logic
The storage directory for data from the real-time message channel can be generated based on the data event time or system time while the storage directory for data from the offline message channel and real-time alert record can be generated based on system time only. The generated archive files will be synchronized to the specified storage system as per the storage path information. When setting the storage path, you can determine the file generation mode by choosing to generate the directory by event time or system time.

<br />

If you choose to generate the directory by the event time, the data content will be parsed and the data event time will be obtained. Next, the data in the same time partition will be written to the same file. Finally, the generated files will be synchronized to the corresponding directory.

<br />

If you choose to generate the directory by the system time, the data in the same time partition will be written to the same file as per the system timestamp and the generated files will be synchronized to the corresponding directory.

## Storage Path Partition Parameters
After specifying the root directory for storing the archive files and the path generation method, you can select different time partition parameter formats. Four time partition parameter formats are supported currently.

<br />

.. list-table::
   :widths: 20 30 50
   :header-rows: 1

   * - Parameter Format
     - Description
     - Example
   * - YYYYMMDD
     - Generate directories by day.
     - /bucketName/samplePath/20190101/
   * - YYYYMMDD/HH
     - Generate directories by day/hour.
     - /bucketName/samplePath/20190101/00/
   * - YYYY/MM/DD
     - Generate directories by year/month/day.
     - /bucketName/samplePath/2019/01/01/
   * - YYYY/MM/DD/HH
     - Generate directories by year/month/day/hour.
     - /bucketName/samplePath/2019/01/01/00/

## Archiving Cycle
Currently, the data archiving policy supports an archiving cycle of 1 hour, 12 housr, or 24 hours. When a data archiving cycle starts, the system starts reading data from the specified message channel. If the archived data falls in the same archiving cycle, the data will be saved in 1 file and sliced by the specified file size if it exceeds the limit.

<br />

However, if no data is cached in a data archiving cycle, no archive file will be generated.

<br />

Different archiving cycles mean different scheduled starting time to trigger the archiving jobs as well as different data range. For example:

<br />

.. list-table::
   :widths: 20 40 40
   :header-rows: 1

   * - Archiving Cycle
     - Scheduled Job Starting Time
     - Archived Data
   * - 1 hour
     - 00:00:00, 01:00:00, 02:00:00, ..., 23:00:00
     - Taking 01:00:00 for example, data to be archived falls in  [00:00:00, 01:00:00).
   * - 12 hours
     - 00:00:00, 12:00:00
     - Taking 12:00:00 PM for example, data to be archived falls in [00:00:00, 12:00:00 PM).
   * - 24 hours
     - 00:00:00
     - Taking 2019-01-02 00:00:00 for example, data to be archived falls in [2019-01-01 00:00:00, 2019-01-02 00:00:00)

.. note:: - The data archiving cycle adopts the system time stamp. If the system time stamp of data is within the current archiving cycle, the data will be archived as per the policy configuration and synchronized to the corresponding storage path.


## Generation of Archived Files

In an archiving cycle, the archiving job will be triggered to generate the archive file only when the first data record arrives. If no data arrives in the archiving cycle, no file or path will be created.

<br />

When **Real-time Message Channel** and **Generate path by event time** are selected in the archiving policy, if the event time of the uploaded data is 1 hour later than the system time or 360 hours earlier than the system time, the archived files will be stored in a folder named `archive_recycling_${filename}` under the specified root directory (in which `filename` is the specified name for the archived file in the policy).

<br />

The columns of the archived file are as follows:

<br />

.. list-table::
   :widths: 40 60
   :header-rows: 1

   * - Field Name
     - Field Description
   * - orgId
     - The organization ID.
   * - modelId
     - The model ID.
   * - assetId
     - The asset ID.
   * - measurepoints
     - The measurement point name.
   * - timestamp
     - The event time of the measurement point.
   * - value
     - The value of the measurement point.
   * - quality
     - The data quality.

<!--end-->
