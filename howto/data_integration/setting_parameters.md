# Setting Parameters for the Data Synchronization Task

<br />

This section shows how to set the parameters in the data synchronization task.

## Available Options for Parameters
You can specify constants, system variables, or custom variables for a parameter.

For more information on the system variables that are available, see [Supported System Variables](../../reference/system_variables).

## Procedure


1. When you are in the data synchronization configuration panel, click **Parameter Settings** at the right edge of the panel.

2. For each parameter that you use, provide the value using the **key=value** format. If you have multiple parameters to define, list each parameter in a new line, for example:

   ```
   key1=value1
   key2=value2
   ```

<br />

The value can be a single value, or an array of values.
<!--Vivian: @weiwei, please list the syntax how to set value array-->

## Example: Using Parameters in the URL

In the example URL below, the `test_list` is a parameter.

  `s3://history/log_solar_dt_change_inverter/${test_list}.each_value`

  <br />

  You can assign values for the parameter as per the following:

  `test_list=Array[20170515,20170516,20170517,20170518,20170519,20170520,20170521,20170522,20170523,20170524,20170808,20170905,20170906,20170918]`

.. image:: media/parameter_example_URL.png
   :alt: Figure: Example parameter settings


<!--end-->
