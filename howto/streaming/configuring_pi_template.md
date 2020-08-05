# Configuring an Electric Energy Calculation Job

<br />

The EnOS Stream Processing Service provides the following templates for calculating electric energy data.

- Electric Energy Cal by Meter Reading
- Electric Energy Cal by Instant Power
- Electric Energy Cal by Average Power

<br />

You can install one or all of the above templates based on your business needs. When creating a stream data processing job, select one of the installed templates to calculate electric energy production or consumption.


## Calculating Electric Energy by Meter Reading

Follow the steps below to complete the configuration when creating a stream data processing job based on the **Electric Energy Cal by Meter Reading** template.

### Calculation Settings

Complete the following calculation settings.

1. The calculation scope **Daily** indicates that the cycle for electric energy calculation is 1 day. When the electric meter data of the next day arrives, the system will output the total electric energy data of the current day.

2. The calculation method **Sum of meter reading delta** accumulates the sum of the electric energy data calculated by meter reading data for all the time intervals of the day. For detailed information about the calculation method, see [Sum of Meter Reading Delta](../../reference/power_calculation_logic#sum-of-meter-reading-delta).

3. Select whether you need the detailed output of the electric energy data by fixed intervals.

### Configuring the Data Processing Policy

In the **Data Processing** section, click **New Strategy** to configure the data processing policy in the pop-up window. Each data processing policy defines the input point, the output point, the slope threshold, and the scale of the electric meter.

1. From the **Input Point** drop-down list, select the model and measurement point that provides the electric meter reading data to be processed. The input point type must be numeric (integer, float, or double).

2. From the **Slope Threshold** drop-down list, select a slope threshold policy to filter out invalid data.

   For example, [0, max] indicates that if the slope of the time interval falls in the range of 0 - max, the electric meter reading data is valid. Invalid data will not be added to the total electric power data. For detailed information about the slope, see [Processing Abnormal Data](../../reference/power_calculation_logic#id2).

   You can specify the slope threshold in the following ways.

   - **Fixed threshold**: Enter fixed values for the threshold. The upper and lower limit values must be greater than or equal to 0, and the lower limit must be less than the upper limit.
   - **Bind to model attribute**: Define the threshold with a model attribute. The lower limit is 0 by default, and the upper limit is defined by the model attribute.

3. From the **Scale** drop-down list, select a format for the electric meter scale. You can specify the scale in the following ways.

   - **Fixed scale**: Enter a numeric value for the scale.
   - **Bind to model attribute**: Define the scale with a model attribute.

4. From the **Daily Output** drop-down list, select a measurement point to store the output of daily electric energy data. The type of the output point must be PI.

5. If "Output by Fixed Interval" is enabled, select the corresponding output point and time interval.

   - **Detailed Output**: Select a measurement point to receive the detailed output. The type of the output point must be PI.
   - **Interval**: Select a time interval for the detailed output.

6. Click **OK** to complete the configuration.

.. note:: - The input point, output point, and the model attributes that are bound to the slope threshold and scale must belong to the same model.
   - The input point, daily output point, and detailed output point cannot be the same point.

### Example

The following example shows the configuration of a typical electric energy calculation job by meter reading data:

.. image:: ../../media/pi_stream_sample.png


## Calculating Electric Energy by Instant Power

Folow the steps below to complete the configuration when creating a stream data processing job based on the **Electric Energy Cal by Instant Power** template.

### Calculation Settings

Complete the following calculation settings.

1. The calculation scope **Daily** indicates that the cycle for electric energy calculation is 1 day. When the electric meter data of the next day arrives, the system will output the total electric energy data of the current day.

2. The calculation method **Integral by instant power** accumulates the sum of the electric energy data calculated by instant power data for all the time intervals of the day. For detailed information about the calculation method, see [Integral by Power](../../reference/power_calculation_logic#integral-by-power).

3. Select whether you need the detailed output of the electric energy data by fixed intervals.


### Configuring the Data Processing Policy

In the **Data Processing** section, click **New Strategy** to configure the data processing policy in the pop-up window. Each data processing policy defines the input point, the output point, the threshold for power data, and the interpolation policy for power data that exceeds the threshold.

1. From the **Input Point** drop-down list, select the model and measurement point that provides the power data to be processed. The input point type must be numeric (integer, float, or double).

2. From the **Threshold** drop-down list, select a threshold policy to filter out invalid data, and enter limit values for the threshold. For example, (0, 12) indicates that if the power data falls in the range of 0 - 12, the power data is valid. Invalid data will be processed by the specified interpolation policy.

3. From the **Interpolation** drop-down list, select the method to process the invalid power data.

   - **LastValue**: Uses the instant power data of the previous time interval to calculate the electric energy of the current time interval.
   - **Ignore**: Ignores the invalid power data, and the electric energy of the current time interval will not be calculated.

4. From the **Daily Output** drop-down list, select a measurement point to store the output of the daily electric energy data. The type of the output point must be PI.

5. If "Output by Fixed Interval" is enabled, select the corresponding output point and time interval.

   - **Detailed Output**: Select a measurement point to receive the detailed output. The type of the output point must be PI.
   - **Interval**: Select a time interval for the detailed output.

6. Click **OK** to complete the configuration.

.. note:: - The input point and output point must belong to the same model. The input point cannot be the output point.
   - The input point, daily output point, and detailed output point cannot be the same point.

### Example

The following example shows the configuration of a typical electric energy calculation job by instant power data.

.. image:: ../../media/instant_power_sample.png



## Calculating Electric Energy by Average Power

Follow the steps below to complete the configuration when creating a stream data processing job based on the **Electric Energy Cal by Average Power** template.

### Calculation Settings

Complete the following calculation settings.

1. The calculation scope **Daily** indicates that the cycle for electric energy calculation is 1 day. When the electric meter data of the next day arrives, the system will output the total electric energy data of the current day.

2. The calculation method **Integral by average power** accumulates the sum of the electric energy data calculated by the average power data for all the time intervals of the day. For detailed information about the calculation method, see [Integral by Power](../../reference/power_calculation_logic#integral-by-power).

3. Select whether you need the detailed output of the electric energy data by fixed intervals.


### Configuring the Data Processing Policy

In the **Data Processing** section, click **New Strategy** to configure the data processing policy in the pop-up window. Each data processing policy defines the input point, the output point, the threshold for power data, and the interpolation policy for power data that exceeds the threshold.

1. From the **Input Point** drop-down list, select the model and measurement point that provides the power data to be processed. The input point type must be numeric (int, float, or double).

2. From the **Threshold** drop-down list, select a threshold policy to filter out invalid data, and enter limit values for the threshold. For example, (0, 12) indicates that if the power data falls in the range of 0 - 12, the power data is valid. Invalid data will be processed by the specified interpolation policy.

3. From the **Interpolation** drop-down list, select the method to process the invalid power data.

   - **LastValue**: Uses the average power data of the previous time interval to calculate the electric energy of the current time interval.
   - **Ignore**: Ignores the invalid power data, and the electric energy of the current time interval will not be calculated.

4. From the **Daily Output** drop-down list, select a measurement point to store the output of daily electric energy data. The type of the output point must be PI.

5. If "Output by Fixed Interval" is enabled, select the corresponding output point and time interval.

   - **Detailed Output**: Select a measurement point to receive the detailed output. The type of the output point must be PI.
   - **Interval**: Select a time interval for the detailed output.

6. Click **OK** to complete the configuration.

.. note:: - The input point and output point must belong to the same model. The input point cannot be the output point.
   - The input point, daily output point, and detailed output point cannot be the same point.

### Example

The following example shows the configuration of a typical electric energy calculation job by average power data.

.. image:: ../../media/average_power_sample.png

## Next Step

[Publishing the Stream Processing Job](publishing_job)
