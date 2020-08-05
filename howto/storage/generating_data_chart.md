# Generating the Time Series Data Chart

<br />

The time series data stored in TSDB can be filtered by parameters and displayed graphically for the quick viewing and analysis of data.

<br />

This section shows how to configure times series data filtering conditions, generate data charts, and quickly view and analyze data.

## Before You Start

- Ensure that the storage policies have been configured for device measurement points, and the measurement point data is of numeric type.
- Ensure that data has been ingested from devices and stored in TSDB.

## Procedure

1. Log in to the **EnOS Management Console**, select **Time Series Data Management > Data Insights**, and configure the data filtering conditions.
2. In the **Select Time Range** section, select or specify the time range for querying data. 
  - 1H: From 1 hour ago to the current moment
  - 1D: From 00:00 of the current day to the current moment
  - 7D: From 00:00 7 days ago to the current moment
  - Customized: Specify the time range
3. Click the **Select Devices** input box, and select one or more devices from the drop-down list. The selected devices will be dynamically shown in the **Selected Measuring Points** column. To reselect devices and clear the list, click **Reset**.
4. In the **Select Data Type** section, select the type of data you want to view. After selecting different data types, the **Selected Measuring Points** column will dynamically display the corresponding measurement point list.
  - If you select **ALL**, the **Selected Measuring Points** column will display all the measurement points of the selected device accordingly. In addition, when querying data, aggregation processing or state change query will not be performed on the measurement point data.
  - If you select the **AI** or **PI** type, you need to also select a data aggregation algorithm and aggregation interval for data querying. The currently supported aggregators are as follows.
       - count: Takes the number of data points in each time range as the result.
       - sum: Takes the sum of the measurement point values in each time range as the result.
       - avg: Takes the average of the measurement point values in each time range as the result.
       - max: Takes the maximum value of the measurement point values in each time range as the result.
       - min: Takes the minimum value of the measurement point values in each time range as the result.
       - first: Takes the first measurement point value in each time range as the result.
       - last: Takes the last measurement point value in each time range as the result.
  - If you select the **DI** type, you need to also select whether to perform state change query for the device status data.
5. In the **Selected Measuring Points** column, click on the selected device name, expand the list of measurement points, and select one or more measurement points to be queried. 


## Results

The queried measurement point data is displayed in the chart on the right. Drag the time line under the chart or use the area zooming tool in the upper right corner of the chart to view detailed information of a specific time range in the chart, including the data timestamp, point name, data value, and data curves.

.. image:: ../../media/data_chart.png

.. note:: For a single measurement point of a single device, the chart can display at most 5,000 data records. To query more, use the corresponding TSDB storage service API.

<br />

Under the data chart, you can view the latest data of the selected measurement points and the last updated time of the data.

.. image:: ../../media/latest_data.png

<br />

Click **Data List** to view the information of the queried data.

.. image:: ../../media/data_list.png

.. note:: For a single measurement point of a single device, the data list can display at most 500 data records. To query more data records, use the corresponding TSDB storage service API.

## Next Steps

### View the Data

To view the data of other devices or measurement points, select the corresponding device name, data type, and measurement point name to query again.

### Download the Data

After viewing the queried measurement point data, you can click the **Download Data** icon |download_icon| to download the queried data. Downloaded data will be saved as `data_insight_{current_date}.csv`. 

.. |download_icon| image:: ../../media/download_icon.png

<!--End-->