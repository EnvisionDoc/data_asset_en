# Data Federation Overview

.. note:: This feature is available for the EnOS 2.1 Update and newer releases.

<br />

EnOS Data Federation provides data querying and file writing services from multi-source heterogeneous data storage systems for application developers and data analysts where users can perform hybrid data querying without worrying about the differences of the query languages used in the various data systems through the use of unified SQL syntax standards, and can write local files to various storage systems quickly with just a simple configuration.

<br />

Other than the above, the Data Federation service also supports OData and JDBC connections, enabling the quick connection to mainstream BI analysis tools such as Tableau and PowerBI regardless of the differences of the source data storage systems.

<br />

The architecture of the Data Federation service is shown as per the below.

<br />

.. image:: ../media/data_federation_arch.png

## Major Concepts

### Channel

The Data Federation service provides a unified data access layer that shields the differences of heterogeneous data sources. Users with different roles can efficiently access data through unified query methods such as standard SQL, JDBC, or OData, thus saving the costs of creating a centralized data warehouse and avoiding the workload and resource waste of massive data replication.

### Channel Type

The Data Federation service supports 2 types of channel: the read channel and the write channel. The read channel supports data query from the specified data source, and the write channel supports data writing to the specified data source.

**Read Channel**

- After configuring and starting the read channel, data from the associated data source can be read through APIs.
- The data sources supported by the read channel include MySQL, Blob, HDFS(EnOS), HIVE(EnOS), KAFKA(EnOS), Redis, and S3.

**Write Channel**

- After configuring and starting the write channel, data can be written to the associated data soruce through the SDK.
- The data sources supported by the write channel include KAFKA(EnOS), MySQL, HDFS(EnOS), and Redis.

### Channel Authorization

The data federation channel support authorization and access authentication functions. After creating a channel, you can give permissions to the designated service accounts to access the channel through the **Channel Auth** page in the **EnOS Management Console**.

## Resource Preparation

<br />

**Data Federation Resource**

Before creating data federation channels, ensure that your OU has requested for the **Data Federation** resource through the **EnOS Management Console > Resource Management** page. The resource specification determines the performance of the data query through the data federation channels, and an allocated resource instance can be associated with only 1 channel. For more information about requesting for the **Data Federation** resource, see [Data Federation Resource Specification](/docs/enos/en/dev/resourcemanagement/reference/data_federation_resource.html).


## Usage Limit

When using the Data Federation service, you need to take note of the following usage limits.

<br />

**Number of Channels**

At most 10 channels (read and write) can be created in an OU.

<br />

**Number of Authorized Applications**

At most 20 applications (service accounts) can be authorized to access data through a single channel.

<br />

**Number of Data Sources**

At most 10 data sources can be associated with a single channel.

<!--end-->
