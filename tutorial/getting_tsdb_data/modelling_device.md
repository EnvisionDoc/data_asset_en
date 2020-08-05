# Unit 1: Modelling the Device

<br />

Create a model with the basic settings below.

- **Identifier**: ElectricMeter
- **Model Name**: ElectricMeter
- **Category**: Grid
- **Created From**: No
- **Source Model**: NA
- **Description**: Model for electric meter

<br />

Define the measurement points for the model.

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Feature Type
     - Name   
     - Identifier   
     - Point Type
     - Description   
   * - Measurement Point
     - Reading
     - Reading
     - AI
     - The original meter reading data.
   * - Measurement Point
     - MaxReading10Min
     - MaxReading10Min
     - AI
     - The maximum reading data in 10 minutes.
   * - Measurement Point
     - MinReading10Min
     - MinReading10Min
     - AI
     - The minimum reading data in 10 minutes.
   * - Measurement Point
     - ReadingDifference
     - ReadingDifference
     - AI
     - The difference between the maximum data and minimum data.

<br />

See the following example:

.. image:: media/measure_points.png



## Next Unit

[Configuring the Storage Policy for the Device Data](configuring_storage_policy)
