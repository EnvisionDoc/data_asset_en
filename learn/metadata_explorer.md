# Data Asset Explorer Overview
The metadata, also known as mediation data and relay data, is the data about data. Metadata is often used to describe objects such as information resources and data, and to provide structured data about the information related to certain resources. The scenarios of exploring asset metadata include identifying resources, evaluating resources, tracking changes of resources in its usage, managing a large volume of networked data efficiently, and achieving effective discovery, query, integration, and effective management of resources.

## Features
Currently, the objects of the data asset exploring feature supported by EnOS are models and measuring points. Metadata of models and measuring point includes basic information, stream processing lineage, TSDB storage configuration, and instance list.

**Stream processing lineage**

The stream processing lineage analytics is used to fully track the data processing flow so as to find all relevant metadata objects that take a data object as the starting point, as well as the relationship between these metadata objects. The relationship between metadata objects refers specifically to the data stream input and output relationship.

In stream data processing jobs, data of measuring points can be calculated and configured. The metadata explorer supports querying the stream processing lineage of the target measuring point, by searching the input and output relationships between all relevant measuring points starting from the target measuring point. The specific functions are described as follows:

- Visualizing the upstream/downstream lineage of measuring points in stream processing jobs
- Viewing the metadata information of any node in the lineage relationship by clicking on a node

**TSDB storage configuration**

TSDB storage policies must be configured for measuring points so that data of the model instances can be stored in TSDB. The metadata explorer supports querying the configured storage policies of measuring points, including the storage policy group, storage type, and storage time.

**Instance list**

You can view all the instances associated with the model to which the measuring point belongs. Besides, cross links to the Data Insights and Data Quality pages are provided for viewing data and data quality details of the queried measuring point of the corresponding instance.

For detailed steps about searching metadata of data assets, see [Querying Metadata of Measuring Points](../howto/metadata/exploring_metadata).