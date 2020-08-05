# Tutorial Overview

## Scenario

In this tutorial, add missing data of a Computer's memory and CPU usage that is stored in TSDB. To get started, we need to register a model, product, and device for a computer, and configure TSDB storage policy for the ``mem_used`` and ``cpu_used`` measurement points. Then, develop a batch data processing workflow with a Python task node to add missing data of the measurement points to TSDB. The added data can be viewed through the Data Insights feature of Time Series Data Management.

<br />

This tutorial walks you through a typical path of writing data to TSDB with a Python task node, that is:

- Registering a computer device to EnOS Cloud.
- Configuring storage policy for the measurement points of the computer.
- Developing a batch data processing workflow with a Python task node.
- Viewing the device measurement point data through Data Insights.

### [Start >](modelling_device)

## Prerequisites

You have requested for **Time Series Database** and **Batch Processing - Container** resources through EnOS Resource Management.

## Units

This tutorial includes the following units:

> [Unit 1. Modelling the Computer Device](modelling_device)
>
> 10 minutes

> [Unit 2. Configuring Storage Policy for Measurement Points](configuring_storage_policy)
>
> 10 minutes

> [Unit 3. Developing a Batch Processing Workflow](developing_workflow)
>
> 30 minutes

> [Unit 4. Viewing Measurement Point Data](viewing_added_data)
>
> 10 minutes
