# Storage Policy Overview

<br />

With the TSDB Storage Policy service, EnOS provides a variety of data storage options based on your data storage and reading requirements. Data can be stored according to categories (data types and storage time), thus reducing data storage costs and enhancing data reading efficiency.

<br />

The figure below shows the processing of how measurement point data that is stored in TSDB.

<br />

.. image:: ../../media/storage_policy_struct.png

## Advantages

You can configure the TSDB storage policy to store important and frequently-accessed data separately by data types. The TSDB storage policy has the following features.

<br />

**Supporting multiple projects or domains**

With the ability to create multiple storage policy groups, the storage policy for different projects or domains can be configured and managed separately. For example, data storage policies of the wind power domain and the solar domain can be configured separately.

.. note:: Each OU can have 2 storage policy groups. Before configuring the storage policy for measurement points, you must associate the asset model with a storage policy group. Each model can be associated with a single storage policy group.

<br />

**Storage by data types**

Data are classified into asset AI type raw data, normalized AI type data, DI type data, PI type data, and generic data to be stored. Specific APIs can be used to get these different types of data.

<br />

**Multiple data sources**

The TSDB can store data that is ingested from connected devices or data that is integrated through the offline message channel.

<br />

**Customized storage time**

The data storage time can be customized based on your business needs (1 month, 3 months, 6 months, 1 year, and several years).

.. note:: The storage time starts from the moment when data is stored in the database. Expired data will be deleted automatically. For example, if *1 year* is selected for the storage time, the database only retains data imported in the past 1 year.

<br />

**Storage policy import and export**

When you need to migrate TSDB storage policy configuration across environment or across OUs, the existing storage policy configuration can be exported and imported into the new environment or OU to realize rapid configuration and deployment.

<br />

**Getting data with API**

EnOS provides open APIs for retrieving data stored in TSDB that have different storage policies. When reading data, the APIs can also run specific functions to process the retrieved data, thus improving the data processing efficiency. For more information about the TSDB data service APIs, go to **EnOS Management Console > EnOS API**.

## Resource Preparation

<br />

**Time Series Database Resource**

Before configuring TSDB storage policies, ensure that your OU has requested for the **Time Series Database** resource through the **EnOS Management Console > Resource Management** page. Otherwise, you cannot create storage policy groups, and the data ingested from devices to EnOS Cloud cannot be stored in TSDB by default. For more information about requesting for the **Time Series Database** resources, see [Time Series Database Resource Specification](/docs/enos/en/dev/resourcemanagement/reference/tsdb_resource.html).

<br />

When you do not need to store asset data in TSDB, you can delete and release the requested Time Series Database Resource throguh the **Resource Management** page to save costs.
