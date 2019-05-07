# Storage Policy

With the Storage Policy service, EnOS provides a variety of data storage options based on your data storage and data reading requirements. Data is stored by categories (data types and storage time), thus reducing data storage costs and enhancing data reading efficiency.

## Features

- **TSDB**: EnOS Time Series Database supports storing important and frequently-accessed data by data types. Asset AI type data, normalized AI type data, DI type data, and generic data can be stored separately, and the data storage time can be customized (1 month, 3 months, 6 months, 1 year, and several years). Each type of the stored data can be retrieved by a specific Open API.
- **Open APIs**: EnOS provides open APIs for retrieving data stored with different storage policies. When reading data, the APIs can also run specific functions to process the retrieved data, thus improving the data processing efficiency.

<!--

**Archive DB**: The Archive database supports storing historical asset data with huge size for a longer time. Data stored in the archive DB can be used for further analysis and generating reports.

-->

## Advantages

- Separate storage policy groups for different projects or domains
- Multiple storage types for different data types
- Flexible data storage time (1 month to 20 years)
- Data service APIs for reading stored data

## Usage Limit

- Currently, each organization can have 2 storage policy groups.
- When storage policy is defined for a measure point, the point type and data type of the measure point cannot be changed. Otherwise, the stored data of the measure point cannot be retrieved by Open APIs.
- The *getAssetsRawDataByTimeRange* API cannot be used to retrieve data of the AI Normalized Data storage type.
