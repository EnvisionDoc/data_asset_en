# Tutorial Overview

## Scenario

In this tutorial, we shall connect a smart electric meter to EnOS Cloud, ingest the meter reading data, and develop stream processing jobs to aggregate the origin meter reading data to get the calculated data that can be used for analysis. Both the origin data and calculated data will be stored in TSDB by the configured storage types and storage time. The stored data can be retrieved with the TSDB Data Service APIs.

<br />

The scenario is in the following chart:

.. image:: media/scenario_stream_tsdb_api.png

<br />

This tutorial will walk you through the typical process of processing and storing the stream data of your devices: 

- Registering and connecting a smart electric meter to EnOS Cloud.
- Configuring the storage policy for the reading data of the electric meter.
- Developing a stream data processing job to calculate the maximum and minimum values of the meter reading data every 10 minutes .
- Developing a stream data processing job to get the difference between the maximum and minimum values of the reading data every 10 minutes.
- Invoking EnOS TSDB Data Service APIs to get the stored meter reading data and calculated data.

### [Start >](modelling_device)

## Prerequisites

- You have completed the [Connecting a Simulated Device to EnOS](/docs/device-connection/en/dev/tutorial/connecting_device_simulated/index.html) tutorial to understand how to connect a device to EnOS and upload the simulated device data to EnOS Cloud.

- You understand how real-time data flows through the engines, the storage, and the applications. For more information, see [Real-time Data Flow](../../learn/data_flow). 

## Units

This tutorial has the following units.

> [Unit 1. Modelling the Device](modelling_device)
>
> 10 minutes

> [Unit 2. Configuring the Storage Policy for the Device Data](configuring_storage_policy)
>
> 10 minutes

> [Unit 3. Registering and Connecting the Device to EnOS](connecting_device)
>
> 20 minutes

> [Unit 4. Developing Stream Data Processing Jobs](developing_streams)
>
> 20 minutes

> [Unit 5. Getting the Stored Data with EnOS APIs](getting_stored_data)
>
> 30 minutes

