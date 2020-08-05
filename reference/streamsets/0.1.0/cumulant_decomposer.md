# Cumulant Decomposer

This stage calculates the delta value between the current record and the last record in the `attr` field and the electric energy data. It has a dependency on the **Last Record Appender** stage.


## Configuration

The configuration tabs for this stage are **General**, **Basic**, and **Input/Output**. 

### General

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Name
     - Yes
     - The name of the stage.
   * - Description
     - No
     - The description of the stage.
   * - Stage Library
     - Yes
     - The streaming calculator library to which the stage belongs.
   * - Required Fields
     - No
     - The fields that the data records must contain. If the specified fields are not included, the record will be filtered out.
   * - Preconditions
     - No
     - The conditions that must be satisfied by the data records. Records that do not meet the conditions will be filtered out.
   * - On Record Error
     - Yes
     - The processing method for error data.

       + Discard: Error data will be discarded and ignored
       + Send to Error: Error messages will be reported
       + Stop Pipeline: The pipeline will be stopped

### Basic

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Quality Filter
     - No
     - Filter the data according to the data quality. Only records that meet the quality conditions will be processed by this stage.


### Input/Output

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Input Point
     - Yes
     - Specify the input point of the records, using the format {modelId}::{pointId}. For the same configuration row, the modelId must be the same, and the input point and the output point must be different.
   * - Scale Type
     - Yes
     - Specify the scale type of the electric energy meter. 

       + 0: Bind to model attribute
       + 1: Fixed scale

   * - Scale
     - Yes
     - Specify the scale of the electric energy meter.

       + Bind to model attribute: Enter the model attribute ID using the format {modelId}::{attributeId}. The data type of the attribute can be float, double, or integer. If the data type of the device instance does not comply with the specification, is null, or the attribute value does not match with the data type, the scale of the electric energy meter will be set to 1 by default.
       + Fixed scale: Enter a value greater than 0 (of type double).

   * - Slope Type
     - Yes
     - Specify the slope threshold type.

       + 0: Bind to model attribute
       + 1: Fixed slope threshold

   * - Min / Max Slope
     - Yes
     - Specify the lower and upper limits of the slope. 

       + Bind to model attribute: The lower limit is 0 by default. For the upper limit, enter the model attribute ID using the format {model}::{attribute}. The data type of the attribute can be float, double, or integer. If the data type of the device instance does not comply with the specification, is null, or the attribute value does not match with the data type, the slope will not be limited.
       + Fixed slope threshold: Enter values for the lower limit and upper limit. The values must be greater than 0 (of type double), and the lower value must be less than the upper value.

   * - Output Point
     - Yes
     - Specify the output point of the records, using the format {modelId}::{pointId}. For the same configuration row, the modelId must be the same, and the input point and the output point must be different.


## Output Results

The specified scale and slope values (fixed value or attribute value) and the calculated record value are included in the `attr` struct.

### Output Example

**With last record**

.. image:: media/delta_calculator_result_1.png

**Without last record**

.. image:: media/delta_calculator_result_2.png

<!--end-->
