# Improving Data Quality
If the data quality is not good enough to meet the business requirements, you can find out potential problems, troubleshoot, and improve data quality by the following ways.

## Checking Device Running Status
Ensure that your devices are running normally and that measuring point data is being uploaded to the cloud:
- On the **Device Management > Device** page, check if the device status is `Online`. 
- On the **Time Series Data > Data Insights** page, check if the latest data of measuring points has been uploaded.

If the device status is `Offline` and measuring point data is not uploaded, check the device running status and the network connection.

## Checking the Configuration of TSDB Storage Policy

Ensure that TSDB storage policy has been configured for the measuring points or that the configuration is not changed by other users.

- On the **Time Series Data > Storage Policy** page, check the storage policy configuration for models and measuring points (storage type and time). 
- On the **Time Series Data > Data Insights** page, test querying data of the measuring points.

## Checking the Status of Stream Processing Jobs

Ensure that the StreamSets pipelines for data quality tagging are running normally.

On the **Stream Data Processing > StreamSets** page, check the running status and processed records (input data and output data) of the data quality tagging pipelines.

<!--end-->

