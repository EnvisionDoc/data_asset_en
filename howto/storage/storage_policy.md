# Storage Policy Overview

With the TSDB Storage Policy service, EnOS provides a variety of data storage options based on your data storage and data reading requirements. Data can be stored by categories (data types and storage time), thus reducing data storage costs and enhancing data reading efficiency.

You can configure TSDB storage policy to store important and frequently-accessed data separately by data types. TSDB storage policy enables:

**Storage policy groups**

Separate storage policy groups for different projects or domains. For example, data storage policies of the wind power domain and the solar domain can be configured separately.

**Storage by data types**

Asset AI type raw data, normalized AI type data, DI type data, PI type data, and generic data can be stored separately. Specific APIs can be used to get data stored as different types.

**Multiple data sources**

TSDB can store data that is ingested from connected devices and that is integrated through the offline message channel.

**Customized storage time**

Data storage time can be customized based on your business needs (1 month, 3 months, 6 months, 1 year, and several years).

**Getting data with API**

EnOS provides open APIs for retrieving data stored with different storage policies. When reading data, the APIs can also run specific functions to process the retrieved data, thus improving the data processing efficiency.
