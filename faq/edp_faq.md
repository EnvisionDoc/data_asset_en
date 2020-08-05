# Frequently Asked Questions

## FAQs for Stream Data Processing


### Q: What preparation work is required before starting a stream processing job?

A: Before running a stream processing job, you need to request for the Stream Processing resources for your organization. Otherwise, the published stream processing jobs cannot be started to process data. You can request for resources of different specifications based on your business needs and the amount of data to be processed. To request for the Stream Processing resources, see [Resource Management on EnOS](/docs/enos/en/dev/resourcemanagement/overview.html).


### Q: Which data types can be processed by the stream processing engine?

A: Currently, you can use the following templates that are provided by the EnOS stream processing engine to quickly create stream processing jobs.

- Time Window Aggregation template: Supports numeric type data aggregation for a single device and single measurement point.
- Multi-Point Merging template: Supports aggregation of data by expressions for a single device and multiple measurement points.
- Electric Energy Calculation by Meter Reading template: Supports electric energy calculation by meter reading data.
- Electric Energy Calculation by Instant Power template: Supports electric energy calculation by instant power data for all the time intervals of the day.
- Electric Energy Calculation by Average Power template: Supports electric energy calculation by average power data for all the time intervals of the day.


### Q: Which time system is used by the stream processing engine, system time or event time?

A: The stream processing engine usually uses the event time, that is, the time when an event occurred. Therefore, the stream processing engine can process disordered event flows and the changing time deviations and calculate meaningful results according to the actual time of events.


### Q: How many stream processing jobs can be created for an organization?

A: Currently, an organization can have at most 50 stream processing jobs.


### Q: Newly published stream processing jobs cannot start running normally. Why?

A: Several reasons might cause the startup failure of stream processing jobs. You can troubleshoot with the following steps.

1. Ensure that your organization has requested got the required computing resources. If there are jobs already running, this reason can be ruled out.
2. If there are running jobs, you can pause one or more jobs and start the new job. The system will allocate computing resources for the new job.
3. Preview the newly published job to ensure that it can run normally. Otherwise, double check the configuration of the stream processing job.

## FAQs for Time Series Data Management

### Q: What preparation work is required before configuring TSDB storage policies?

A: Before configuring TSDB storage policies, you need to request for the Time Series Database resource for your organization. Otherwise, the configured TSDB storage policies will not take effect by default. To request for the Time Series Database resources, see [Resource Management on EnOS](/docs/enos/en/dev/resourcemanagement/overview.html).


### Q: When should I configure TSDB storage policies?

A: It is recommended that you configure TSDB storage policies after your devices are connected to the IoT hub and before device data is ingested. Otherwise, the ingested data will not be stored in TSDB by default. If you want to store the data that is processed by the streaming engine, you must configure the TSDB storage policies for the processed data before the stream processing jobs start running.


### Q: How many storage policy groups can be created for an organization?

A: Currently, an organization can have at most 2 storage policy groups.


### Q: Can attributes of models and measurement points that are associated with TSDB storage policies be modified?

A: When TSDB storage policies are configured, the associated measurement point ID, measurement point type, and data type cannot be modified. Otherwise, the stored data cannot be retrieved with EnOS TSDB data service APIs.


### Q: My devices are connected and have started uploading data to the cloud. Why could I not get data through the data service API?

A: After device connection, you need to configure TSDB storage policies for your device measureement points. Otherwise, the ingested data will not be stored in TSDB by default, and you cannot get the data with API.


### Q: Can data stored in TSDB be deleted?

A: Data stored in TSDB can be deleted with the **Data Deletion** feature. For more information, see [Deleting Data in TSDB](/docs/data-asset/en/dev/howto/storage/clearing_data.html).


### Q: When archiving data, which external storage systems are supported?

A: Currently, archived data can be synchronized to the Azure Blob storage.


## FAQs for Data Subscription

### Q: How many data subscription jobs can be created for an organization?

A: Currently, an organization can have at most 15 data subscription jobs.


### Q: How many partitions does a single Kafka topic have?

A: A single Kafka topic has 2 partitions. That is, a topic can support 2 data consumers at the same time.


### Q: How long will subscribed data be stored in Kafka topics?

A: By default, subscribed data will be stored in Kafka topics for 3 days.


### Q: How can I get the subscribed data after configuring the data subscription jobs?

A: You can call the data subscription functions with the EnOS data subscription SDK to push the subscribed data to your application. For the sample code for getting the subscribed data, see [Consuming Subscribed Data](/docs/data-asset/en/dev/howto/obtain/consuming_subscribed_data.html).
