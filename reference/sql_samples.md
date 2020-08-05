# SQL Statement Samples

The Federation Query product supports querying data from data sources by entering SQL statements. The SQL statements must comply with the SQL92 standard. Commonly used SQL statements are:

- ``show schemas``: View the schemas of all data sources that are defined by the data federation channels.

- ``describe {full_table_path}``: Query the table structure (if the tables are not of csv format, it might not be able to display the structure).

- ``select {* / column_name} from {table_name} where {column_name} operator {value}``: Query the rows and columns in a table.


## SQL Statement Samples

The following table shows SQL statement samples for querying data from various data sources:

.. list-table::
   :widths: 10 30 30 30
   :header-rows: 1

   * - Data Source
     - Table Structure
     - Sample Configuration
     - SQL Samples
   * - MySQL
     - data_source.database.table
     - + Data Source Name: mysql_private
       + Database Name: test_database
       + Table Name: test_table
     - + show tables from mysql_private.test_database
       + select * from mysql_private.test_database.test_table2017-05-26
   * - Hive
     - data_source.database.table
     - + Data Source Name: hive_enos
       + Database Name: db_keytab
       + Table Name: test_table
     - + show tables from hive_enos.db_keytab
       + select * from hive_enos.db_keytab.test_table
   * - Redis
     - data_source.db.type
     - + Data Source Name: redis_private
       + Database Name: db0
     - + show tables from redis_private.db0
       + select * from redis_private.db0
   * - HDFS
     - data_source.folder0.folder1.file0 (The file sysytem is different from that of databases. The file structure is data source, folders, and files.)
     - + Data Source Name: hdfs_enos
       + Folder Name: folder0
       + File Name: test.csv
     - + show files from hdfs_enos
       + show files from hdfs_enos.`/folder0`
       + select * from hdfs_enos.`/folder0/file1`
   * - S3/Blob
     - data_source.bucket.folder1.file0 (S3 and Blob are also file systems, but with buckets.)
     - + Data Source Name: s3_private
       + bucket Name：enos
       + Folder Name: folder0
       + File Name: test.csv
     - + show files from s3_private.enos
       + show files from s3_private.enos.`/folder0`
       + select * from s3_private.enos.`/folder0/file1`
   * - Kafka
     - data_source.topic (Kafka is different from other data sources. It has data source and topics only.)
     - + Data Source: kafka_enos
       + Topic: MEASURE_POINT_INTERNAL_o15815849618351
     - + show tables from kafka_enos
       + select * from kafka_enos.MEASURE_POINT_INTERNAL_o15815849618351

## Commonly Used ``select`` Example

```
select {* / column_name} from {table_name} where {column_name} operator {value}

select * from stock_information where stockid = str(nid)
stockname = 'str_name'
stockname like '% find this %'
stockname like '[a-zA-Z]%'
stockname like '[^F-M]%'

or stockpath = 'stock_path'
or stocknumber < 1000
and stockindex = 24
not stock*** = 'man'
stocknumber between 20 and 100
stocknumber in(10,20,30)
order by stockid desc(asc)
order by 1,2
stockname = (select stockname from stock_information where stockid = 4)

select distinct column_name form table_name
select stocknumber ,"stocknumber + 10" = stocknumber + 10 from table_name
select stockname , "stocknumber" = count(*) from table_name group by stockname
having count(*) = 2

select *
from table1, table2
where table1.id *= table2.id
table1.id =* table2.id

select stockname from table1
union [all]
select stockname from table2
```


## Commonly Used Functions

### Statistical Functions

- AVG
- COUNT
- MAX
- MIN
- SUM
- STDEV()
- STDEVP()
- VAR()
- VARP()


### Arithmetic Functions

**Trigonometric Functions**

- SIN(float_expression)
- COS(float_expression)
- TAN(float_expression)
- COT(float_expression)


<br />

**Functions for INTEGER/MONEY/REAL/FLOAT**

- EXP(float_expression)
- LOG(float_expression)
- LOG10(float_expression)
- SQRT(float_expression)


<br />

**Functions for Approximate Values**

- CEILING(numeric_expression)
- FLOOR(numeric_expression)
- ROUND(numeric_expression)
- ABS(numeric_expression)
- SIGN(numeric_expression)
- PI()
- RAND([integer_expression])


<br />

**String Functions**

- ASCII()
- CHAR()
- LOWER()
- UPPER()
- STR()

<br />

**Data Functions**

- DAY()
- MONTH()
- YEAR()
- DATEADD(<datepart>,<number>,<date>)


<!--end-->
