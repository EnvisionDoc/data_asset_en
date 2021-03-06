# Terminology

<br />

This section introduces the major concepts involved in the EnOS Enterprise Data Platform.

## Stream Data

Broadly speaking, the generation of data can be considered as a series of discrete events. When drawing these discrete events on a time axis, an event stream or data stream is formed. Stream data consists of these endless event streams.

<br />

Both offline data and stream data are normally sent as logs. Unlike traditional offline data, stream data is generated continuously from many data sources. However, the size of the stream data is normally smaller than that of the offline data.

<br />

The devices connected to a data center, the telemetry data of devices, and the log files generated by mobile or web applications are some common sources of stream data.

## Data Type

Data ingested from different devices and sensors are of different types. The EnOS Stream Processing Service supports the analysis and storage of multiple types of data, such as AI, DI, PI, and generic types. The data types of these measurement points are defined when creating device models.

## Data Storage

Data ingested from devices or integrated from offline message channels, after being processed by the stream processing engine, can be stored in the target storage system based on the configured storage policies. According to the data types and usage, data can be stored in different systems, for different storage durations, and be retrieved by different methods.  

## Data Subscription

EnOS provides the data subscription service to help users obtain and use real-time device data efficiently. When data subscription jobs are running, the data subscription service will push the subscribed data to the users' applications automatically. The subscribed data includes real-time device data and alert data.



<!--end-->
