# EnOS Stream Processing Service Overview

<br />

Powered by Apache Spark™ Streaming, and customized and optimized by Envision, the EnOS Stream Processing engine has high scalability, high throughput, and high fault-tolerance. EnOS Stream Processing Service aims to help you cope with the velocity, volume, and variety of data by increasing the data development and access efficiency, enforcing data quality and compliance, and optimizing data storage, thereby reducing your total cost of ownership on your IoT data.

<br />

 EnOS Stream Processing service also accumulates common algorithms for processing IoT data. Application developers can develop stream data processing jobs through simple template configuration. In addition, EnOS Stream Processing Service provides a number of data processing templates and calculators in the energy field, helping data engineers to develop data processing solutions quickly without coding, greatly improving the efficiency of data development and reducing the development threshold.

<br />

The major components and architecture of EnOS Stream Processing service is shown in the figure below.

<br />

.. image:: ../../media/streaming_arch.png

<br />

The EnOS Stream Processing Service can be used in the following scenarios:

- **Aggregating and calculating asset raw data**

  You can filter the raw data received from devices, aggregate the data by a certain algorithm, and save the aggregated data for further processing.  

- **Computation of device states**

  You can obtain certain state parameters of a device to confirm its status. The stream processing framework maintains the state of devices and sites internally and the system updates both the measurement point values and the device connection status to the latest state.

- **Customized stream data processing**

  You might need to handle complex stream data processing in some business scenarios. EnOS Stream Processing Service provides a set of underlying packaged StreamSets calculators for developers to develop customized stream data processing jobs to meet the requirements of various business scenarios.


## Data Processing Flow

EnOS Stream Processing Service procedure is as follows.

1. **Process raw data**

   The original measurement point data is sent to Kafka through the EnOS connection layer. The messages received are analyzed by the stream computing service. Before processing, the data is filtered according to the specified threshold. The data exceeding the threshold will be processed by the interpolation algorithm.

2. **Perform calculation**

   In this step, the data is computed by the defined algorithm in the processing strategy.

3. **Store computed output**

   The data from the streaming module flows into In-memory Database (IMDB) and Kafka, and the downstream continues to subscribe to all data from Kafka and record them to the Time Series Database (TSDB) or other storage systems. The stored data can be used as the data source for offline data processing and further processing and analysis.


## Features

EnOS Stream Processing Service provides the following major features.

<br />

**Real-time and Unbounded Stream Data Processing**

A website log, a type of stream data, for example, records data as long as the website is online. This stream data is thus real-time and unbounded. As the data is generated continuously, the data streams are integrated to the streaming system continuously as well. The data that the streaming data processing engine processes is therefore real-time and unbounded, where the data streams are subscribed and consumed by the stream processing service in chronological order.

<br />

**Continuous and Efficient Computation**

The computation mode of of EnOS Stream Processing Service is “event triggered”. The trigger is the unbounded stream data mentioned in the previous section. Once new stream data is sent to the system, the system immediately initiates and performs a computation task. Therefore, stream computing is a continuous process and is very efficient.

<br />

**Stream and Real-time Data Integration**

The calculated results of stream computing triggered by stream data is recorded continuously into the destination data storage, based on the configured data storage policies.

<br />

**Calculation Templates for the Energy Industry**

The EnOS Stream Processing Service provides data calculation templates for the energy industry. You can install the templates based on your business needs, and then use the templates for configuring stream data processing jobs quickly.

- Time Window Aggregation template
- Electric Energy Cal by Meter Reading template
- Electric Energy Cal by Instant Power template
- Electric Energy Cal by Average Power template

<br />

**StreamSets Calculator Library**

The EnOS Stream Processing Service provides a set of underlying packaged StreamSets calculator libraries. After installing a StreamSets calculator library, you can develop customized stream data processing jobs to meet the requirements of your business scenarios. For more information, see the [StreamSets Calculator Documentation](../../reference/streamsets/index).


## Resource Preparation

<br />

**Stream Processing Resource**

Before installing the stream data processing templates and StreamSets calculator libraries, or before configuring stream data processing jobs, ensure that your OU has requested for the **Stream Processing** resource through the **EnOS Management Console > Resource Management** page. The resource specification determines the performance of stream data processing jobs. For more information about requesting for the **Stream Processing** resources, see [Stream Processing Resource Specification](/docs/enos/en/dev/resourcemanagement/reference/stream_data_processing.html).

<br />

When you do not need to process stream data with the Stream Processing service, you can delete and release the requested Stream Processing resource through the **Resource Management** page to save costs.
