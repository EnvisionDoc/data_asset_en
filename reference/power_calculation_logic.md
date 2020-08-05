# Electric Energy Calculation Logic

<br />

Electric energy calculation is one of the most common calculation scenarios in the energy industry, and it has strict requirements for the accuracy of the calculation. Therefore, the processing of abnormal data such as drastic changes in electric meter data and power data is quite important. The EnOS stream processing engine integrates abnormal data processing into the calculation process to ensure the accuracy of the electric energy data.

## Sum of Meter Reading Delta

The Electric Energy Calculation by Meter Reading template uses the "Sum of meter reading delta" calculation method to calculate daily electric energy data with the following steps.

1. Obtain the electric energy data of each time interval (delta of electric meter readings in the time interval).
2. Calculate the daily electric energy data by summing up the delta of all the time intervals of the day.

<br />

The calculation method is illustrated in the figure below.


.. image:: ../media/electric_power_delta.png

- Input: Electric meter readings (`kWh`)
- Time interval: The time range from `t1` through `t2` (`Hour`)
- Electric energy data in the time interval: `Delta(EEnergy)=kWh2-kWh1`

### Calculation Logic

The detailed logic for calculating electric energy data of different situations is as follows.

#### Data changes in a time interval

Check whether the slope of the time interval falls in the threshold `[0,slope_max]`:

- If Yes, the electric energy data of this time interval will be added to the daily value: `DailyData=Sum(EEnergy)*scale`. The system will record the latest electric meter reading data (kWh) and the end time of the interval (Hour), which will be used as the starting point for the slope of the next time interval.
- If No, the electric energy data of this time interval will not be added to the daily value. The system will also record the latest electric meter reading data (kWh) and the end time of the interval (Hour), which will be used as the starting point for the slope of the next time interval.

#### Data does not change in a time interval

Within the time interval, the electric meter reading does not change. The system does not record the end time of the interval.

.. image:: ../media/electric_power_logic_1.png

As the figure above shows, the electric meter reading does not change from t2 through t3. When new data arrives at t4, the time interval for calculation of the slope and electric energy data is from t2 to t4.

#### Calculation across 0'clock

Generally, the uploaded electric meter reading will cross 00:00 as shown in the following figure.

.. image:: ../media/electric_power_logic_2.png

Therefore, the electric energy data calculation of the previous day will end at t1, and the data calculation for the current day will start from t1.

### Constant Parameters

In electric energy calculation, the following constant parameters are determined by the business and devices.

- Electric meter accuracy (digits)
- Slope threshold
- Electric meter scale
- Electric energy unit (kWh)

### Processing Abnormal Data

In the electric energy data chart, the slope of the curve in a time interval can be used to filter out abnormal data. Different electric meters allow different slope values. For example, [0, max] indicates that if the slope of a time interval falls in the range of 0 - max, the electric meter reading data of the time interval is valid. Invalid data will not be added to the total electric energy data.

<br />

The calculation method of the slope is: `slope=Delta(EEnergy)/Delta(Time)`

.. image:: ../media/electric_power_slope.png

If the slope exceeds a certain range, it may be caused by a drastic change in electric meter data or by negative electric energy data (an extreme case is that the electric meter reading is reset to zero). This will break the monotonous increasing law of the chart curve.

.. image:: ../media/electric_power_minus_slope.png


## Integral by Power

The Electric Power Calculation by Power templates uses the "Integral by instant / average power" (with the unit of kW or W) calculation method to calculate daily electric energy data, with the following calculation logic.

- Input: Power data ingested from a measurement point (`kW` or `W`)
- Time interval: The time range from `t1` through `t2` (`Hour`)
- Electric energy data in the time interval: `EEnergy=ActivePower*Time`

The power data can be instant power data at a time point or average power data within a time interval.

### Calculation Logic

The calculation logic for different power data types are as follows.

#### By instant power data

In a time interval, the measurement point ingests the instant power data at a time point. For example, in the following figure, the power data for the past 3 minutes is the instant power value at P1.

.. image:: ../media/electric_power_logic_3.png

Therefore, the electric energy data for time interval `t1` through `t2` is: `EEnergy=P1*(t2-t1)`.

#### By average power data

In a time interval, the measurement point ingests the average power data within a time interval, for example, in the following figure, the average power for the past 3 minutes.

.. image:: ../media/electric_power_logic_4.png

For easier calculation, we shall use the simple arithmetic average value of P1 and P2 to calculate the electric energy.

.. image:: ../media/electric_power_logic_5.png

Therefore, the electric energy data for time interval `t1` through `t2` is:  `EEnergy=(P1+P2)/2*(t2-t1)`.

### Processing Abnormal Data

In actual situations, data might be lost, exceed the threshold, or duplicated.

- Data lost, but the data uploading frequency can be estimated.
- Data exceeded threshold, or changing rate exceeded limit.
- Duplicated data (time stamp and point value are both duplicated).

<br />

For the atypical situations above, data needs to be processed to ensure that there is no big deviation in the electric energy calculation result.

<br />

As the power data is of AI type, we can process the data first by the following procedure, and then calculate the electric energy data (an extra measurement point is needed to receive the normalized power data):

.. image:: ../media/electric_power_exception.png

<!--end-->
