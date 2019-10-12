# Storage Policy Overview

With the TSDB Storage Policy service, EnOS provides a variety of data storage options based on your data storage and data reading requirements. Data can be stored by categories (data types and storage time), thus reducing data storage costs and enhancing data reading efficiency.

The following figure shows the flow of measuring point data that is stored in TSDB based on storage policy configuration:

.. image:: ../../media/storage_policy_struct.png

## Advantages

You can configure TSDB storage policy to store important and frequently-accessed data separately by data types. TSDB storage policy enables:

**Supporting multiple projects or domains**

With separate storage policy groups, storage policy for different projects or domains can be configured and managed separately. For example, data storage policies of the wind power domain and the solar domain can be configured separately.

.. note:: Each OU can have 2 storage policy groups. Before configuring storage policy for measuring points, you must associate the asset model with a storage policy group. Each model can be associated with a single storage policy group.

**Storage by data types**

Asset AI type raw data, normalized AI type data, DI type data, PI type data, and generic data can be stored separately. Specific APIs can be used to get data stored as different types.

**Multiple data sources**

TSDB can store data that is ingested from connected devices and that is integrated through the offline message channel.

**Customized storage time**

Data storage time can be customized based on your business needs (1 month, 3 months, 6 months, 1 year, and several years).

.. note:: The storage time starts from the moment when data is stored in the specific database. Expired data will be deleted automatically. For example, if *1 year* is selected for the storage time, the database only retains data imported in the last 1 year.

**Getting data with API**

EnOS provides open APIs for retrieving data stored in TSDB with different storage policy. When reading data, the APIs can also run specific functions to process the retrieved data, thus improving the data processing efficiency. For more information about the TSDB data service APIs, go to **EnOS Console > EnOS API**.
