# Tutorial Overview

## Scenario

In this tutorial, synchronize data from an external MySQL database (with some employee information) to EnOS Hive periodically, so that the employee data can be further processed and analyzed with data analytics tools provided by EnOS.

<br />

The scenario is depicted in the following chart:

.. image:: media/integrating_external_data.png

<br />

This tutorial walks you through a typical path of integrating external data sources into EnOS, which is:

- Registering the external data source
- Creating a target Hive table to receive data to be synchronized from the external database
- Creating and configuring a data synchronization task with periodic scheduling to synchronize data periodically
- Running the data synchronization task
- Viewing the synchronized data in the Hive table

### [Start >](configuring_data_connection)

## Prerequisites

You have data stored in an external MySQL database, which is ready to be integrated into EnOS Hive table.

## Units

This tutorial includes the following units:

> [Unit 1. Registering Data Source](configuring_data_connection)
>
> 10 minutes

> [Unit 2. Creating a Target Hive Table](creating_hive_table)
>
> 20 minutes

> [Unit 3. Configuring a Data Synchronization Task](creating_data_integration_task)
>
> 20 minutes

> [Unit 4. Running the Data Synchronization Task](running_data_integration_task)
>
> 20 minutes

> [Unit 5. Viewing the Synchronized Data](viewing_synchronized_data)
>
> 5 minutes
