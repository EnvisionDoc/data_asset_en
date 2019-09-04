# Viewing Data Quality Report
By marking data with quality information tags, you can query the quality report of the data. The data quality reports provide data quality information in 3 dimensions: completeness, accuracy, and timeliness, helping you quickly understand the data quality of your assets.

## Prerequisites
The prerequisites for querying data quality reports are as follows:
- TSDB storage policies have been configured for device measuring point data.
- The device measuring point data has been marked by quality tags with the Streamsets quality rule Stages.

## Setting Query Conditions for Quality Report 
After logging in the EnOS Console, select **Data Quality** from the left navigation panel, enter the following query conditions, and click the **Query** button:

.. image:: ../../media/data_quality_filter.png

- **Model**: Select the model to be queried. Support for selecting all public and private models under the current organization.
- **Measuring Point**: Select the measuring point to be queried under the selected model. Currently, it is supported to query the daily quality report for a single measuring point.
- **Asset**: Select 1 or multiple assets. Support for querying quality reports of multiple assets under the same model.
- **Time**: Select or customize a certain period of time (days) to query the quality report. To avoid large amount of queried data, the current query limit is: number of assets * days ≤ 600.

## Viewing Data Quality Report

After the data quality report is generated, you can view the data quality details from the following dimensions:

### Quality dimensions

- Completeness 

  View the daily completeness data of the measuring point data. Currently, only the number of measuring points that upload data is counted (depending on the number of data points stored in TSDB).

  .. image:: ../../media/data_quality_completeness.png

- Accuracy 

  View the daily accuracy rate of measuring point data. Accuracy rate = Accurate points / Total points.

  > Accuracy of data is determined by judging whether the measuring point value exceeds the specified threshold range. If the value exceeds the upper limit, the data will be marked over-upper-limit tag; if the value exceeds the lower limit, the data will be marked over-lower-limit tag. Data marked by tags will be deemed as inaccurate.
  >
  > .. image:: ../../media/data_quality_accuracy.png

- Timeliness 

  View the daily timeliness rate of measuring point data. Timeliness rate = Timely points / Total points.

  > Timeliness of data is determined by comparing the time stamp of each uploaded data point with the time stamp of the latest data of the measuring point. If the time stamp of the uploaded data is later than the time stamp of the latest data, the data will be marked as late; if it is earlier than the time stamp of the latest data, the uploaded data will not be marked as late, and the time stamp of the latest data is replaced with that of the current data.
  >
  > .. image:: ../../media/data_quality_timeliness.png

### Color marking for abnormal quality

Different levels of data quality are marked with different colors in the data quality report to facilitate rapid identification of abnormal data:

- 0 -20%: red
- 20 -50%: orange
- 50 - 80%: blue
- ≥80%: transparent

### Toggling between point count/percentage

Click **Point Count** or **Percentage** to toggle how the data quality report data is presented.

### Downloading quality report

Click the **Download** icon |download_icon| to download and save the data quality report.



.. |download_icon| image:: ../../media/download_icon.png

<!--end-->

