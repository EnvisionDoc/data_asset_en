# Accessing Data Sources by Python

<br />

This section describes how to access HDFS, Hive, Kafka, S3, and Blob data sources by Python.

## Success and Failure Judgement

Define a ``main`` function that contains the return value:

```
def main():
    print(1)
    return 0
```

<br />

The following example shows a successful task, returning 0:

```
def main():
    print(‘The task runs successfully’)
    return 0
```

<br />

Task failure can be the following situations:

- Return value is not 0.
- The program throws an exception, which causes the program to fail to run.

For example：

```
def main():
    print(‘The task fails’)
    return 'fail'

def main():
    print(‘The task fails’)
    return -1

def main():
    print(‘The task fails’)
    raise Exception(‘raise exeception, let task fail’)
```

## HDFS

Use the following methods to access HDFS by Python:

```
import hdfs
def main():
    #List files under the root directory of HDFS of the current OU.
    res = hdfs.listDir('/')
    if res == 0:
        return 0
    else:
        return -1

import hdfs
def main():   
    #Upload a local file to HDFS.
    #res = hdfs.appendFile('File path on HDFS','Local file path')
    #In the following example, if /test/put1 already exists, append the content of file xia_20200522.txt #to file /test/put1.
    res = hdfs.appendFile('/test/put1','/home/envuser/etl/xia_20200522.txt')
    if res == 0:
        return 0
    else:
        return -1

import hdfs
def main():
    #Append content to a file on HDFS.
    #In the following example, if file '/test/put1' does not exist, it will be created automatically.
    #By default, the appended content does not include line feeds. Otherwise, add line feeds to the file #header.
    #res = hdfs.appendContent('File path','Appended content')
    res = hdfs.appendContent('/test/put1','add some content')
    if res == 0:
        return 0
    else:
        return -1

import hdfs
def main():
    #Upload a local file /home/envuser/etl/put3 to the /user/db_hongtao_hao/test directory on HDFS.
    #res = hdfs.put('File path on HDFS','Local file path')
    hdfs.put('/test','/home/envuser/etl/put3')
    if res == 0:
        return 0
    else:
        return -1

import hdfs
def main():
    #Create a directory.
    res = hdfs.mkdir('/test')
    if res == 0:
        return 0
    else:
        return -1
```

## Hive

Use the following methods to access Hive by Python:

```
import hive
def main():
    #Run an execute statement, returning 0 upon success.
    #The execute statement can be used to run statements such as insert, create, load, and drop.
    rs = hive.execute('''load data inpath '/testfile/emp.txt' into table emp''')
    if res == 0:
        return 0
    else:
        return -1

import hive
def main():
    #Run an executeUpdate statement, returning the number of impacted lines.
    #The executeUpdate statement can be used to run statements such as insert, update, and delete.
    #Returning a value less than 0 upon failure. Returning 0 or a value greater than 0 upon success.
    #Returning the number of imapcted lines, but needs to be determined by the SQL statements.
    rs = hive.executeUpdate('''insert into emp values('a','b')''')
    if res >= 0:
        return 0
    else:
        return -1

import hive
def main():
    #Run an executeQuery statement, returning ResultSet.
    #This statement can be used for query statements.
    rs = hive.executeQuery('select count(*) from emp')
    while rs.next():
        print(rs.getInt(1))
    return 0
```

## Kafka

Use the following methods to access Kafka by Python:

```
from Msg import MsgBuilder,MeasurepointBuilder

import batchTSDBWriter

def main():
    #Build measurement point data. If timestamp is not provided, the current timestamp will be used as #the default value.
    
    mp1 = MeasurepointBuilder.builder().add_measurepoint("MeasurePoint11", 100).add_measurepoint("MeasurePoint12", "aa");
    mp2 = MeasurepointBuilder.builder().add_measurepoint("MeasurePoint21", 100).add_measurepoint("MeasurePoint22", "aa").set_timestamp(1542609276270);

    #Provide the OU ID, model ID, and asset ID.
    #Use set_modelIdPath to provide the model ID path.
    #Use add_payload to upload the measurement point data.
    #Use set_dq to initialize data quality.
    #Use add_dq to append data quality.

    msg = MsgBuilder.builder("1b47ed98d1800000","inverter","zabPDuHq")set_modelIdPath("/").add_payload(mp1).add_payload(mp2)

    #str(msg) is the message to be sent to Kafka.
    #The first parameter is of Boolean type. When False is specified, measurepoints will not be validated.
    #The second parameter is of Boolean type. When False is specified, assetId will not be validated.
    #The length of message must not exceed 3000 bytes.

    res = batchTSDBWriter.send_data(str(msg),False,False)
    if res == 0:
        return 0
    else:
        return -1
```

## S3

Use the following methods to access S3 by Python:

```
import s3Wrapper

def main():
    s3_session = s3Wrapper.conn(ID of S3 data source in the current OU)
    #s3_session can be used for a series of operations.
    for bucket in s3_session.buckets.all():
        print('bucket name:%s'%bucket.name)
    return 0
```

## Blob

Use the following methods to access Blob by Python:

```
import blobWrapper

def main():
    container_client = blobWrapper.conn(ID of Blob data source in the current OU)
    blob_list = container_client.list_blobs('commonfs')
    #blob_list can be used for a series of opertions.
    for blob in blob_list:
        print("\t" + blob.name)
    return 0
```

<!--end-->
