# Configuring SHELL Type Task Node

Batch Processing supports multiple frameworks such as Hive, Spark, MapReduct, etc. When creating a workflow, you can add SHELL task nodes to develop data. 

<br />

This section shows how to configure SHELL task nodes.


## Executing HiveSQL Tasks

You can implement batch computing by using SHELL task nodes to execute HiveSQL tasks through the command line.

### Command Format

```
canaanhive [arguments]
```

### Parameter Description

.. list-table::
   :widths: 30 30 40
   :header-rows: 1

   * - Parameter
     - Example
     - Description
   * - -f <arg>
     - -f demo.sql
     - The HQL file name.
   * - -d <arg>
     - -d 2018-01-01
     - The time parameter. In this example, the `${env.FORMAT}` in the HQL file will automatically be replaced according to format in the **Time Parameter Format** table below.
   * - -E <paraN>=<valN>
     - -E para=abc
     - The user-defined parameter assigned in the HQL file. In this example, the `${env.para}` in the HQL file will automatically be replaced with `abc`.
   * - -str <sql>
     - -str "show tables;"
     - The SQL statement.

<br />


.. list-table:: Time Parameter Format
   :widths: 30 30 40
   :header-rows: 1

   * - FORMAT
     - Range
     - Value
   * - YYYYMMDD
     -
     - 2018-01-01
   * - YYYYMMDD_PnD
     - 1<= n <=30
     - 2017-12-31 ~ 2017-12-02
   * - YYYYMMDD_PnM
     - 1<= n <=12
     - 2017-12-01 ~ 2017-01-01
   * - YYYYMMDD_PnY
     - 1<= n <=2
     - 2017-01-01 ~ 2016-01-01
   * - YYYYMMDD_NnD
     - 1<= n <=2
     - 2018-01-02 ~ 2018-01-03
   * - YYYYMMDD_NnM
     - 1<= n <=2
     - 2018-02-01 ~ 2018-03-01
   * - YYYYMMDD_NnY
     - 1<= n <=2
     - 2019-01-01 ~ 2020-01-01
   * - YYYYMM
     -
     - 2018-01
   * - YYYYMMDD_PnD
     - 1<= n <=2
     - 2017-12 ~ 2017-12
   * - YYYYMMDD_PnM
     - 1<= n <=2
     - 2017-12 ~ 2017-11
   * - YYYYMMDD_PnY
     - 1<= n <=2
     - 2017-01 ~ 2016-01
   * - YYYYMMDD_NnD
     - 1<= n <=2
     - 2018-01 ~ 2018-01
   * - YYYYMMDD_NnM
     - 1<= n <=2
     - 2018-02 ~ 2018-03
   * - YYYYMMDD_NnY
     - 1<= n <=2
     - 2019-01 ~ 2020-01
   * - YYYY
     -
     - 2018
   * - YYYY_PnD
     - 1<= n <=2
     - 2017 ~ 2017
   * - YYYY_PnM
     - 1<= n <=2
     - 2017 ~ 2017
   * - YYYY_PnY
     - 1<= n <=2
     - 2017 ~ 2016
   * - YYYY_NnD
     - 1<= n <=2
     - 2018 ~ 2018
   * - YYYY_NnM
     - 1<= n <=2
     - 2018 ~ 2018
   * - YYYY_NnY
     - 1<= n <=2
     - 2019 ~ 2020
   * - MM
     -
     - 01
   * - DD
     -
     - 01

### Examples

With the command line in the SHELL node as per the following:

```
canaanhive -f demo.sql -d 2018-01-01 -E DB=demo
```

<br />

And an HQL file `demo.sql` having the following sample code:

```
use ${env.DB};
create table if not exists demo(id string);
insert into demo values('${env.YYYYMMDD}');
```

<br />

The executed content will be:

```
use demo;
create table if not exists demo(id string);
insert into demo values('2018-01-01');
```

## Executing Spark Tasks

You can execute PySpark and Spark tasks through the command line by using SHELL task nodes.

### Command Format

Using a PySpark Job as an example, create a SHELL type node and use the SHELL command to run the main function of the Job.

```
sh predict.sh
```

### Submitting a PySpark Job

```
submit-pyspark-application    [options]      <python file>     [app arguments]
```

#### Parameter Description

.. list-table::
   :widths: 30 70
   :header-rows: 1

   * - Parameter
     - Description
   * - --python 2.7/3.5
     - The Python version, supports 2.7 or 3.5. The default is 2.7.
   * - --pythonEnvPath
     - The VirtualEnv path In HDFS. If not set, the default Python envrionment will be used.
   * - --name NAME
     - The name of your application.
   * - --queue QUEUE_NAME
     - The YARN queue to submit to (Default: "default").
   * - --num-executors NUM
     - The number of executors to launch (Default: 2). If dynamic allocation is enabled, the initial number of executors will be at least _NUM_.
   * - --executor-cores NUM
     - The number of cores per executor. (Default: 1 in YARN mode, or all available cores on the worker in standalone mode.)
   * - --driver-cores NUM
     - The number of cores used by the driver, only in cluster mode (Default: 1).
   * - --conf PROP=VALUE
     - The arbitrary Spark configuration property.
   * - --py-files PY_FILES
     - The comma-separated list of .zip, .egg, or .py files to place on the PYTHONPATH for Python apps.
   * - --files FILES
     - The comma-separated list of files to be placed in the working directory of each executor.
   * - --archives ARCHIVES
     - The comma-separated list of archives to be extracted into the working directory of each executor.
   * - --driver-memory MEM
     - The memory for the driver (e.g. 1000M, 2G) (Default: 2G).
   * - --driver-java-options
     - The extra Java options to pass to the driver.
   * - --driver-library-path
     - The extra library path entries to pass to the driver.
   * - --driver-class-path
     - The extra class path entries to pass to the driver. Note that jars added with --jars are automatically included in the classpath.

### Submitting a Spark Job

```
submit-spark-application    [options]      <app-jar>     [app arguments]
```

#### Parameter Description

.. list-table::
   :widths: 30 70
   :header-rows: 1

   * - Parameter
     - Description
   * - --class CLASS_NAME
     - Your application's main class (for Java / Scala apps).
   * - --name NAME
     - The name of your application.
   * - --packages
     - The comma-separated list of Maven coordinates of jars to include on the driver and executor classpaths. The local maven repo will be searched, and the Maven central and any additional remote repositories will be given by the `--repositories` option. The format for the coordinates should be groupId:artifactId:version.
   * - --jars JARS
     - The comma-separated list of local jars to include on the driver and executor classpaths.
   * - --conf PROP=VALUE
     - The arbitrary Spark configuration property.
   * - --files FILES
     - The comma-separated list of files to be placed in the working directory of each executor.
   * - --archives ARCHIVES
     - The comma-separated list of archives to be extracted into the working directory of each executor.
   * - --driver-memory MEM
     - The memory for the driver (e.g. 1000M, 2G) (Default: 2G).
   * - --driver-java-options
     - The extra Java options to pass to the driver.
   * - --driver-library-path
     - The extra library path entries to pass to the driver.
   * - --driver-class-path
     - The extra class path entries to pass to the driver. Note that jars added with --jars are automatically included in the classpath.
   * - --executor-cores NUM
     - The number of cores per executor. (Default: 1 in YARN mode, or all available cores on the worker in standalone mode.)
   * - --driver-cores NUM
     - The number of cores used by the driver, only in cluster mode (Default: 1).
   * - --queue QUEUE_NAME
     - The YARN queue to submit to (Default: "default").
   * - --num-executors NUM
     - The number of executors to launch (Default: 2). If dynamic allocation is enabled, the initial number of executors will be at least _NUM_.

### Examples

Using the example command to run the main function `predict.sh` in the SHELL node:

```
sh predict.sh
```

<br />

The example code for the main function is:

```
submit_pyspark_application_func(){
    submit-pyspark-application \
    --deploy-mode cluster \
    --queue ${1} \
    --name pyspark_predict_test \
    --num-executors 10 \
    --driver-memory 16g \
    --executor-memory 12g \
    --driver-cores 2 \
    --executor-cores 3 \
    --conf spark.eventLog.enabled=true \
    --conf spark.network.timeout=240000 \
    --conf spark.executor.heartbeatInterval=24000 \
    --conf spark.yarn.executor.memoryOverhead=8192 \
    --archives hdfs://user/db_test/userPythonLib.zip#ANACONDA  \
    --conf spark.yarn.appMasterEnv.PYSPARK_PYTHON=./ANACONDA/MINICONDA/bin/python \
    --conf spark.yarn.maxAppAttempts=1 \
    --conf spark.logger_table=wens_status_algo_running \
    --conf spark.hdfs_user=${2} \
    --conf spark.hdfs_path=hdfs://titan/user/${2} \
    --conf spark.start_date=${3} \
    --conf spark.end_date=${4} \
    --conf spark.site_ids=${5} \
    --conf spark.metric_save_path=/user/${2}/operaphm_temperature/metrics \
    --py-files anomaly.py,hadoop_common_functions.py,layout.py,utm.zip,rle.py,common_tools.py,steadystatefilter.py,math_utils.py \
    --conf spark.eventLog.enabled=true  predict.py
}

echo "test"
```

<br />

In the above, `predict.py` is the incoming py file, and needs to be in the same directory as `predict.sh`.


<!--end-->
