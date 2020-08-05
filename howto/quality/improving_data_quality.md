# Improving the Data Quality

<br />

If the data quality is not good enough to meet the business requirements, you can find the potential problems, troubleshoot, and improve data quality via the following ways.

## Checking the Device Running Status
To see whether your devices are running normally and the measurement point data is being uploaded to the cloud, do the following.
- On the **Asset Management > Device Asset** page, check if the device status is `Online`.
- On the **Time Series Data Management > Data Insights** page, check if the latest data of the measurement point has been uploaded.

<br />

If the device status is `Offline` and the measurement point data is not uploaded, check the device running status and the network connection.

## Checking the Configuration of TSDB Storage Policy

To see whether the TSDB storage policy has been configured for the measurement points or the configuration has been changed by other users, do the following.

- On the **Time Series Data Management > Storage Policy** page, check the storage policy configuration for models and measurement points (storage type and time).
- On the **Time Series Data Management > Data Insights** page, test query the data of the measurement points.

## Checking the Status of Stream Processing Jobs

To see whether the StreamSets pipelines for data quality tagging are running normally, do the following.

<br />

On the **Stream Processing > StreamSets** page, check the running status and processed records (input data and output data) of the data quality tagging pipelines.

<!--end-->
