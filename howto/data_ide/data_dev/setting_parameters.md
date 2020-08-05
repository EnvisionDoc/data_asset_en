# Setting Parameters for a Workflow or SHELL-type of Task

<br />

This section shows how to set the parameters when you configure a workflow or task.

## Available Options for Parameters
You can specify constants, system variables, or custom variables for a parameter.

See [Supported System Variables](../../../reference/system_variables) for the system variables that can be used.

## Procedure

1. When you are in the workflow or task configuration panel, click **Parameter Settings** at the right edge of the panel.

2. For each parameter that you use, provide the value using the **key=value** format. If you have multiple parameters to define, list each parameter in a new line, for example:

```
key1=value1
key2=value2
```

<br />

The value can be a single value, or an array of values.
<!--Vivian: @weiwei, please list the syntax how to set value array-->

## Example: Using Parameters in SHELL script

The following shows an example where parameters are used in the SHELL script.

```
java -cp ide.sdk-0.1.3.jar com.envision.dataplatform.C2R.C2RBeelineUtil -i
${inputPath}  -o ${outputPath} -ot ${outputTableName} -ca ${columnAll} -cm
${columnMust} -cs ${columnSelected} -g ${group_name} -h "${HIVE_JDBC}" -u
${unix_timestamp} -z ${time_zone}
```

<br />

You can assign values for the parameters as per the following:

```
inputPath=/user/hive/warehouse/xiaoxiao_product_db.db/input
outputPath=/tmp/xiaoxiao/output
outputTableName=2018_07_31
columnAll=projectid,deviceid,updatetime,envi_monitor_pm1,envi_monitor_pm25
columnMust=projectid,deviceid,updatetime,
columnSelected=envi_monitor_pm1,envi_monitor_pm25
time_zone=Asia/Shanghai
```

<br />

.. image:: ../media/parameter_example_SHELL.png
   :alt: Figure: Example parameter settings

<!--end-->
