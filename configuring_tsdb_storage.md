# Configuring TSDB Storage

EnOS Time Series Database (TSDB) enables you to store and retrieve important and frequently-accessed business data. TSDB provides specific storage types for different types of business data. Each storage type has specific data storing and reading capability. You can define customized data storage policies based on your business needs. Currently, EnOS TSDB provides the following storage types:

- AI Raw Data
- AI Normalized Data
- DI Data
- PI Data
- Generic Data

## Configuring AI Raw Data Storage Type

AI (analogy input) data consists of physical parameters like temperature, pressure, flow, etc. The values of these parameters are collected by various sensors, converted to electric signals by a transmitter, and transferred to the analogy input of the controller. To reflect real-time data changes, AI data generally has high ingestion frequency, usually by seconds, and thus having huge data size. In most business cases, the second-level raw data is usually normalized by minute-level processing, so this kind of second-level raw data does not need to be stored for a long time.

Features of the AI Raw Data storage type are as follows:

| Feature              | Description                                                  |
| :------------------- | :----------------------------------------------------------- |
| Data type            | AI type data only (the data type is selected when defining a measuring point) |
| Data source          | Measuring point raw data uploaded to the cloud (or normalized data processed by the streaming engine) |
| Storage time         | Based on business needs (it is recommended to select a short storage time due to the huge data size) |
| API for reading data | *Get Asset AI Raw Data* (getting the stored AI raw data of certain measuring points of specified assets in a time range) |

Take the following steps to configure AI Raw Data storage type:

1. Log in EnOS Console, click **Storage Policy > TSDB Storage**, and select the created storage policy group.

2. Move the cursor on the **AI Raw Data** storage type and click the **Edit** icon to open the **Edit Storage Policy** page.

3. From the **Storage Time** drop down list, select the storage time for your data.

4. Select models and the corresponding measuring points for which the data storage policy serves.

5. Click **OK** to save the storage policy. See the following example.

   .. image:: media/storage_policy_config_1.png

## Configuring AI Normalized Data Storage Type

As described in the above section, the second-level raw data is usually normalized by minute-level processing in most business cases to reduce the data size. EnOS TSDB stores the normalized data separately and supports extra processing for the stored data. When you retrieve the minute-level normalized data with API, EnOS TSDB provides aggregation functions for further data processing.

Features of the AI Normalized Data storage type are as follows:

| Feature                  | Description                                                  |
| :----------------------- | :----------------------------------------------------------- |
| Data type                | AI type data only (the data type is selected when defining a measuring point) |
| Data source              | Normalized data processed by the streaming engine (or measuring point raw data uploaded to the cloud) |
| Normalization processing | If the data source is AI raw data, the second-level suffix of the data timestamp will be removed when the data is stored in TSDB. Therefore, only the last-coming data record of a minute will be stored. |
| Storage time             | Based on business needs (can be a longer time due to the smaller data size) |
| API for reading data     | *Get Asset AI Data with Aggregation Logic* (getting the stored minute-level normalized AI data of certain measuring points of specified assets in a time range) |
| Aggregation functions    | TSDB provides aggregation functions for further processing the stored data when retrieving data with the *Get Asset AI Data with Aggregation Logic* API. Supported aggregation functions are `cnt`, `avg`, `sum`, `max`, `min`, `first`, and `last`. Note that if data aggregation logic is NOT used, the value of the `interval` parameter must be 0. |

The configuration of the **AI Normalized Data** storage type is similar with that of the **AI Raw Data** storage type. See the following example.

.. image:: media/storage_policy_config_2.png

## Configuring DI Data Storage Type

DI (digital Input) data is usually used for recording device status. For example, a sensor outputs the device running status, such as water flow switch and wind speed switch. The switch status is transferred to the controller and then converted to digital value 1 or 0, which can be used for logic analysis and computation. DI data is usually enumerable status values, and the frequency of data upload is not fixed. Generally, data is upload or stored only when device status changes. For DI data, EnOS TSDB provides separated storage and reading policy.

Features of the DI Data storage type are as follows:

| Feature              | Description                                                  |
| :------------------- | :----------------------------------------------------------- |
| Data type            | DI type data only (the data type is selected when defining a measuring point) |
| Data source          | Measuring point raw data uploaded to the cloud               |
| Storage time         | Based on business needs (can be a long time due to the small data size) |
| API for reading data | *Get Asset DI Data* (Getting the status change data of specified assets in a time range) |

The configuration of the **DI Data** storage type is similar with that of the **AI Raw Data** storage type.



## Configuring PI Data Storage Type

PI (pulse input) data is usually used for power meter readings. For PI data, EnOS TSDB provides separated storage and reading policy.

Features of the PI Data storage type are as follows:

| Feature              | Description                                                  |
| :------------------- | :----------------------------------------------------------- |
| Data type            | PI type data only (the data type is selected when defining a measuring point) |
| Data source          | Minute-level normalized PI data (If the measuring point data is second-level raw data, the suffix of the data time stamp will be removed when the data is stored in TSDB) |
| Storage time         | Based on business needs (can be a longer time due to the smaller data size) |
| API for reading data | *Get Asset Electric Power Data* (Getting the stored PI data of certain measuring points of specified assets in a time range); *Get Asset Current Day Electric Power* (Getting the current day electric power data of specified assets, starting from 00:00 of the current day) |

The configuration of the **PI Data** storage type is similar with that of the **AI Raw Data** storage type.



## Configuring Generic Data Storage Type

When configuring device models, you can choose AI, DI, PI, or Generic as the data type of a measuring point. EnOS TSDB provides separate storage policy for generic data.

Features of the Generic Data storage type are as follows:

| Feature              | Description                                                  |
| :------------------- | :----------------------------------------------------------- |
| Data type            | Generic type data only (the data type is selected when defining a measuring point) |
| Data source          | Measuring point raw data uploaded to the cloud               |
| Storage time         | Based on business needs                                      |
| API for reading data | *Get Asset Generic Data* (getting the generic data of certain measuring points of specified assets in a time range.) |

The configuration of the **Generic Data** storage type is similar with that of the **AI Raw Data** storage type.

## TSDB Storage Resources

After configuring TSDB storage policies, you need to ensure that TSDB storage resources have been allocated for your organization. Otherwise, the configured storage policies will not take effect, and the device data will not be stored by default. To request TSDB storage resources, see [Managing Resources](/docs/enos/en/2.0.8/resourcemanagement/getstarted.html).

<!--end-->
