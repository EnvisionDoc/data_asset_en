# Configuring a Multi-Point Data Calculation Job

<br />

You can use the **Multi-Point Merging** template to quickly create a stream processing job for calculating the data of multiple measurement points and assign the processed data to another measurement point on the same device by writing customized calculation expressions.

## Setting the Triggering Mode

The Multi-Point Merging template currently supports two types of triggering modes. The triggering mode can be set in the **Triggering Mode** section.

- **Triggering by point**

  From the **Mode** drop-down list, select *point*, and from the **Timing Interpolation** drop-down list, select *LastValue*.

  When the data of the triggering point arrives, the data processing task will be triggered. The data timestamp of the triggering point will be used as the timestamp of the output record.

  If the data of a measurement point does not arrive when a data processing task is triggered, the latest data record of the measurement point will be used for calculation. This is how **Timing Interpolation** works.   

- **Triggering by frequency**

  From the **Mode** drop-down list, select *frequency*, and from the **Triggering Frequency** drop-down list, select a frequency value.

  The data processing job will be triggered by the specified frequency. The system time of EnOS stream processing engine is used for controlling the trigger.

## Configuring the Data Processing Policy

In the **Data Processing** section, click **New Strategy** to configure the data processing policy in the pop-up window.

<br />

When the triggering mode is *point*, the configuration of a data processing policy record is as follows.

1. From the **Output Point** drop-down list, select the measurement point that receives the output value of the data processing expression. Supported data types include integer, float, string, and bool (other types will be converted to string).

2. From the **Triggering Point** drop-down list, select the measurement point to trigger the data processing strategy.

3. In the **Output Logic** field, type the data processing expression. For the supported syntax, see [Multi-Point Merging Expression Syntax](../../reference/statement_syntax).

4. Click **Check Syntax** to verify the data processing expression that you entered.

5. Click **OK** to complete the configuration.

   .. note:: The triggering point, output point, and the measurement points and attributes used in the data processing expression must belong to the same model. The triggering point cannot be the output point.

<br />

When the triggering mode is *frequency*, the configuration of a data processing policy record is as follows.

1. From the **Output Point** drop-down list, select the measurement point that receives the output value of the data processing expression. Supported data types include integer, float, string, and bool (other types will be converted to string).

2. In the **Output Logic** field, type the data processing expression. For the supported syntax, see [Multi-Point Merging Expression Syntax](../../reference/statement_syntax).

3. Click **Check Syntax** to verify the data processing expression that you entered.

4. Click **OK** to complete the configuration.

## Example

The following example shows the configuration of a typical multi-point data merging job:

.. image:: ../../media/multi_point_stream_sample.png

## Next Step

[Publishing the Stream Processing Job](publishing_job)
