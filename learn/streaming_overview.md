# The EnOS Stream Processing Service

<br />

Powered by Apache Spark™ Streaming, and customized and optimized by Envision, the EnOS Stream Processing engine has high scalability, high throughput, and high fault-tolerance.

<br />

The EnOS Stream Processing Service can be used in the following scenarios:

- Aggregating and calculating asset raw data

  You can filter the raw data received from devices, aggregate the data by a certain algorithm, and save the aggregated data for further processing.  

- Computation of device states

  You can obtain certain state parameters of a device to confirm its status. The stream processing framework maintains the state of devices and sites internally and the system updates both the measurement point values and the device connection status to the latest state.

## Features

**Real-time and unbounded stream data processing**

A website log, a type of stream data, for example, records data as long as the website is online. This stream data is thus real-time and unbounded. As the data is generated continuously, the data streams are integrated to the streaming system continuously as well. The data that the streaming data processing engine processes is therefore real-time and unbounded, where the data streams are subscribed and consumed by the stream processing service in chronological order.

<br />

**Continuous and efficient computation**

The computation mode of of EnOS Stream Processing Service is “event triggered”. The trigger is the unbounded stream data mentioned in the previous section. Once new stream data is sent to the system, the system immediately initiates and performs a computation task. Therefore, stream computing is a continuous process and is very efficient.

<br />

**Stream and real-time data integration**

The calculated results of stream computing triggered by stream data is recorded continuously into the destination data storage, based on the configured data storage policies.

## Data Processing Flow

The EnOS Stream Processing Service procedure is as follows.

1. Process the raw data

   The original measurement point data is sent to Kafka through the EnOS connection layer. The messages received are analyzed by the stream computing service. Before processing, the data is filtered according to the specified threshold. The data exceeding the threshold will be processed by the interpolation algorithm.

2. Perform calculation

   In this step, the data is computed by the defined algorithm in the processing strategy.

3. Store the computed output

   The data from the streaming module flows into In-memory Database (IMDB) and Kafka, and the downstream continues to subscribe to all data from Kafka and record them to the Time Series Database (TSDB) or other storage systems. The stored data can be used as the data source for offline data processing and further processing and analysis.

## Data Processing Templates

The EnOS Stream Processing Service provides the following templates for developers to configure stream data processing jobs quickly.

- Time Window Aggregation
- Multi-Point Merging
- Electric Energy Cal by Meter Reading
- Electric Energy Cal by Instant Power
- Electric Energy Cal by Average Power

## StreamSets Operators

The EnOS Stream Processing Service provides a set of underlying packaged StreamSets operators for developers to design customized stream data processing jobs to meet the requirements of complex business scenarios. For more information, see the [StreamSets Calculator Documentation](../reference/streamsets/index).

## Resource Preparation

**Stream Processing Resource**

Before installing the stream data processing templates and StreamSets calculator libraries, or before configuring stream data processing jobs, ensure that your OU has requested for the **Stream Processing** resource through the **EnOS Management Console > Resource Management** page. The resource specification determines the performance of stream data processing jobs. For more information about requesting for the **Stream Processing** resources, see [Stream Processing Resource Specification](/docs/enos/en/dev/resourcemanagement/reference/stream_data_processing.html).
