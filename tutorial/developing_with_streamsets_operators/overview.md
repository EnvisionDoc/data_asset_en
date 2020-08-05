# Tutorial Overview

## Scenario

In this tutorial, we shall connect the wind turbines of a wind farm to EnOS Cloud, upload the energy production meter reading data to the cloud, and develop a stream processing pipeline to aggregate the meter reading data to get the daily energy production of each wind turbine, the total energy production of the wind farm, and the carbon reduction data of the wind farm. Both the original data and calculated data will be stored in TSDB by the configured storage types and storage time.

<br />

This tutorial will walk you through the typical process of developing a stream data processing job with StreamSets operators for complex business scenarios:

- Registering and connecting wind turbines to EnOS Cloud.
- Configuring the storage policy for the origin and calculated data.
- Developing a stream data processing job with StreamSets operators to calculate the daily energy production and carbon reduction of a wind farm.
- Viewing the origin data and calculated data with Data Insights.

### [Start >>](modelling_device)

## Prerequisites

- You have completed the [Connecting a Simulated Device to EnOS](/docs/device-connection/en/dev/tutorial/connecting_device_simulated/index.html) tutorial to understand how to connect a device to EnOS and upload simulated device data to EnOS Cloud.

- You understand how real-time data flows through the engines, the storage, and the applications. For more information, see [Real-time Data Flow](../../learn/data_flow).

- You know the basic steps of creating a stream data processing pipeline with StreamSets calculators. For more information, see [Developing with StreamSets Calculators](../../howto/stream/streamsets).

## Units

This tutorial has the following units.

> [Unit 1. Registering and Connecting Wind Turbines to EnOS Cloud](modelling_device)
>
> 30 minutes

> [Unit 2. Configuring the Storage Policy for the Origin and Calculated Data](configuring_storage_policy)
>
> 10 minutes

> [Unit 3. Connecting Wind Turbine Devices to EnOS](connecting_device)
>
> 20 minutes

> [Unit 4. Developing a Stream Data Processing Job](developing_streams)
>
> 40 minutes

> [Unit 5. Viewing the Stored Data with Data Insights](viewing_stored_data)
>
> 10 minutes
