# Data Archiving Reference

## Data Archiving Logic<logic>
The storage directory for data from the real-time message channel can be generated based on data event time or system time. The storage directory for data from the offline message channel can be generated based on system time only. The generated archive files will be synchronized to the specified storage system as per the storage path information. When setting the storage path, you can determine the file generation mode by selecting to generate the directory by event time or system time.

If you select to generate the directory by the event time, the data content will be parsed and the data event time will be obtained. Then, the data in the same time partition will be written to the same file. Finally, the generated files will be synchronized to the corresponding directory. If you select to generate the directory by the system time, the data in the same time partition will be written to the same file as per the system time stamp of data. Finally, the generated files will be synchronized to the corresponding directory.

## Storage Path Partition Parameters<path>
After specifying the root directory for storing the archive files and the path generation method, you can select different time partition parameter formats. Four time partition parameter formats are supported currently, which are described as follows:

.. list-table::
   :widths: 20 30 50

   * - Parameter Format
     - Description
     - Example
   * - YYYYMMDD
     - Generating directories by day
     - /bucketName/samplePath/20190101/
   * - YYYYMMDD/HH
     - Generating directories by day/hour
     - /bucketName/samplePath/20190101/00/
   * - YYYY/MM/DD
     - Generating directories by year/month/day
     - /bucketName/samplePath/2019/01/01/
   * - YYYY/MM/DD/HH
     - Generating directories by year/month/day/hour
     - /bucketName/samplePath/2019/01/01/00/

## Archiving Cycle<cycle>
Currently, the data archiving policy supports 1 hour as the archiving cycle. When a data archiving cycle starts, the system starts reading data from the specified message channel. If the archived data falls in the same archiving cycle, the data will be saved in 1 file and sliced by the specified file size.

However, if no data is cached in a data archiving cycle, no archived file will be generated.

<!--

Different archiving cycles mean different scheduled starting time to trigger the archiving jobs as well as different data range. For example:

.. list-table::
   :widths: 20 40 40

   * - Archiving Cycle
     - Scheduled Job Starting Time
     - Archived Data
   * - 1 hour
     - 00:00:00, 01:00:00, 02:00:00, ..., 23:00:00
     - Taking 01:00:00 for example, data to be archived falls in  [00:00:00, 01:00:00).
   * - 6 hours
     - 00:00:00, 06:00:00, 12:00:00, 18:00:00
     - Taking 6:00:00 AM for example, data to be archived falls in [00:00:00, 6:00:00 AM).
   * - 12 hours
     - 00:00:00, 12:00:00
     - Taking 12:00:00 PM for example, data to be archived falls in [00:00:00, 12:00:00 PM).
   * - 24 hours
     - 00:00:00
     - Taking 2019-01-02 00:00:00 for example, data to be archived falls in [2019-01-01 00:00:00, 2019-01-02 00:00:00)

.. note:: - The data archiving cycle adopts the system time stamp. If the system time stamp of data is within the current archiving cycle, the data will be archived as per the policy configuration and synchronized to the corresponding storage path.

-->

## Generation of Archived Files<file>

The logic of generating archived files is as follows:

In an archiving cycle, the archiving job will be triggered to generate the archived file only when the first data record arrives. If no data arrives in the archiving cycle, no file or path will be created.

When **Real-time Message Channel** and **Generate path by event time** are selected in the archiving policy, if the event time of the uploaded data is 1 hour later than the system time or 360 hours earlier than the system time, the archived files will be stored in a folder named `archive_recycling_${filename}` under the specified root directory (in which `filename` is the specified name for the archived file in the policy).

The columns of the archived file are as follows:

.. list-table::
   :widths: 40 60

   * - Field Name
     - Field Description
   * - orgId
     - Organization ID
   * - modelId
     - Model Identifier
   * - assetId
     - Asset ID
   * - measurepoints
     - Measuring point name
   * - timestamp
     - Event time of measuring point
   * - value
     - Value of measuring point
   * - quality
     - Data quality

<!--end-->
