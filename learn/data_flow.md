# Real-time Data Flow

Real-time data that is processed by EnOS Stream Analytics can be viewed through 3 layers, the engine layer, the storage layer, and the application layer.

## Engine Layer

When assets are connected into the EnOS cloud, the asset raw data is ingested through the IoT Hub. After the data is ingested into the IoT Hub:

1. The **Rule Engine** routes the streams of data in Kafka message queue as topics.

2. The asset raw data is routed to the **Origin Data Topic**, and the data processed by the streaming engine is routed to the **Cal Data Topic**.

3. The data processing logics of the Streaming Engine include 2 parts:

   - User-defined logic: you can design real-time data processing streams through the **Stream Development** function in the EnOS Console.

     For more information about designing data processing jobs, see [Developing Stream Processing Jobs](/howto/stream/index).  

   - System logic: the system built-in logic that completes operations like data format conversion.

See the following illustration of data flow in the engine layer:

.. image:: ../media/data_flow_1.png

## Storage Layer

EnOS provides a variety of data storage options based on data types and data reading requirements. 

TSDB is suitable for storing important and frequently-accessed data by data types. Data to be stored can be ingested from connected devices or integrated through the offline message channel. Data to be stored can be ingested from connected devices or integrated through the offline message channel. Asset AI type data, normalized AI type data, DI type data, PI type data, and generic data can be stored separately. 

The Data Connector service supports archiving business data of huge size and lower access frequency. Data to be archived can be ingested from connected devices or integrated through the offline message channel. The archived files will be synchronized to target database and stored in the specified file path, thus achieving data backup.

Data in the Origin Data Topic and the Cal Data Topic are written to **In-memory Database (IMDB)**, **Time Series Database (TSDB)**, and **Data Archiving (Archive)** storage.

- IMDB: stores only the latest data for fast query.

- TSDB: stores time series data of specified time range based on the storage policies that you define in the EnOS Console. The stored data can be retrieved through TSDB Data Service APIs.

- Archive: archives asset data based on the data archiving policy that you define in the EnOS Console.


For more information about TSDB storage, see [Configuring TSDB Storage](../configuring_tsdb_storage). For more information about Data Connector, see [Configuring Data Archiving Jobs](../howto/archive/configuring_archive_storage).

See the following illustration of data flow in the storage layer:

.. image:: ../media/data_flow_2.png

## Application Layer

You can subscribe to both the original data and the calculated data, so that the asset data can be consumed by your applications directly. The subscription settings can be configured through the **Data Subscription** function in the EnOS Console, and EnOS provides Java SDK for retrieving the subscribed data. For more information about data subscription, see [Developing Data Subscription Jobs](../howto/obtain/managing_data_subscription).

See the following illustration of data flow in the application layer:

.. image:: ../media/data_flow_3.png

<!--end-->
