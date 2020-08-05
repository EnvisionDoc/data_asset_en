# Reading and Writing Data

<br />

After an application is authorized to access data through the created channel, you can call the data federation APIs to read data from or write data to data sources through the channel.

## Prerequisites

- A channel is created and is running.
- The application is authorized to access data through the channel.

## Reading Data

You can call the data federation _Read Data_ API to query data from data sources using SQL query. For more information about the Data Federation Service APIs, go to **EnOS Management Console > EnOS APIs**.

### SQL Query Example

```
show schemas
```

<br />

### Response Sample

```
{
    "status": 0,
    "msg": "success",
    "submsg": null,
    "data": {
        "queryState": "COMPLETED",
        "columns": [
            "SCHEMA_NAME"
        ],
        "metadata": [
            "VARCHAR"
        ],
        "rows": [
            {
                "SCHEMA_NAME": "mysql196.test1"
            },
            {
                "SCHEMA_NAME": "mysql196.test2"
            }
        ]
    }
}
```

<br />

This SQL query example is used to get the data source schemas. In the response sample, ``mysql196`` is the customized alias for the data source that was given when creating the data federation channel. ``test1`` and ``test2`` are the names of the databases in the data source.

<br />

When querying data, use ``mysql196.test1`` as the MySQL database name. The syntax of SQL query for getting data from the data sources is similar with MySQL syntax. For example:

```
select * from mysql196.test1.user limit 100
```

## Writing Data

You can call the data federation _Write Message_ API to write data to data sources. For more information about the Data Federation Service APIs, go to **EnOS Management Console > EnOS APIs**.

### Writing Data to MySQ Data Source

The data format for writing data to MySQL is as per the below.

```

{
  "dataSourceName": "data_source_name",
  "data":{
    "table": "table_name",
    "lines": [
      {
        "column_name": "value"
      }
    ]
  }
}
```

<br />

In which:
- ``dataSourceName``: The data source name.
- ``data``: The data to be written to the data source (must be converted to JSON).
- ``table``: The table name to write the data.
- ``lines``: The lines of data to be written to the data source.(``column_name`` is name of a field, and the ``value`` must be converted to JSON).

<br />

For example:

```
{
    "dataSourceName": "mysql_remote",
    "data": "{\"table\":\"data\",\"lines\":[{\"WGEN.GenReactivePW\":\"2.5283\",\"ou_id\":\"o15622268182161\",\"WTUR.TurbineListSts\":\"5\",\"WTUR.TurbineUnionSts\":\"71\",\"WTUR.ConnectionSts\":\"0\",\"WGEN.GenActivePW\":\"45.700001\",\"WROT.TemB2Mot\":\"29.504801\",\"WTUR.TurbineTopSts\":\"2\",\"WGEN.TorqueSetpoint\":\"867.359375\",\"WWPP.PPCurrentDay\":\"0\",\"WCNV.GridFreq\":\"49.971561\",\"WWPP.PPCurrentYear\":\"17896\",\"dev_id\":\"04mmQAEM\",\"WNAC.TemOut\":\"25.691801\",\"WWPP.PPCurrentMonth\":\"33763\",\"WTUR.TurbineHealthSts\":\"0\",\"timeOfDay\":\"2019-09-01 00:00:00\",\"WTUR.TurbineGroupSts\":\"70\"},{\"WGEN.GenReactivePW\":\"2.7037\",\"ou_id\":\"o15622268182161\",\"WTUR.TurbineListSts\":\"5\",\"WTUR.TurbineUnionSts\":\"71\",\"WTUR.ConnectionSts\":\"0\",\"WGEN.GenActivePW\":\"45.439999\",\"WTUR.TurbineTopSts\":\"2\",\"WGEN.TorqueSetpoint\":\"865.127869\",\"WCNV.GridFreq\":\"49.998112\",\"dev_id\":\"04mmQAEM\",\"WTUR.TurbineHealthSts\":\"0\",\"timeOfDay\":\"2019-09-01 00:00:01\",\"WTUR.TurbineGroupSts\":\"70\"}]}"
}
```

### Writing Data to Redis Data Source

The data format for writing data to Redis is as per the below (currently only KV data structure is supported).

```
{
  "dataSourceName": "data_source_name",
  "data":{
    "item": [
      {
        "key": "key",
        "value": "value"
      }
    ]
  }
}
```

<br />

In which:
- ``dataSourceName``: The data source name.
- ``data``: The data to be written to the data source (must be converted to JSON).
- ``item``: The collection of "key-value" pairs to be written to the data source (``value`` must be converted to JSON).

<br />

For example:

```
{
    "dataSourceName": "redis_remote",
    "data": "{\"item\":[{\"key\":\"04mmQAEM\",\"value\":\"1180\"},{\"key\":\"1jbWuJA7\",\"value\":\"964\"}]}"
}
```


<!--end-->
