# Off Limit Tagger

This stage supports the filtering of data with the specified threshold values. The specific logic is as follows:

- Input data with the specified lower limit and upper limit values (Outlier Detection) are filtered.
- Verify if the value of the `record.measurepoint.value` field in the record falls in the specified `min,max` range.
  - If the data value does not fall in the range, the value of the `/attr/isOutlier` field in the output is set to `true`.
  - If the data value falls in the range, the value of the `/attr/isOutlier` field in the output is set to `false`.
- The configured threshold values and parameters will be included in the `/attr/outlierAttr` field as output.


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
     - Specify the input point of the records, using the format {modelId}::{pointId}.
   * - OpenClose
     - Yes
     - Select the format of the threshold. 
     
       + (x,y)
       + (x,y]
       + [x,y)
       + [x,y]
       + (-∞,y)
       + (-∞,y]
       + (x,+∞)
       + [x,+∞)
       + (-∞,+∞)

   * - Min-Max
     - Yes
     - Specify the lower limit value and upper limit value of the threshold, separated by comma.
   * - Output Point
     - Yes
     - Specify the output point of the records, using the format {modelId}::{pointId}. After processing the values of the input point with the threshold, the streaming engine will tag records that exceed the upper or lower limit and output the tagging results to the output point.


## Output Results

The output results of this stage are included in the `attr` struct. The description of the fields are as follows:

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Data Type
     - Description
   * - isOutlier
     - Boolean
     -
   * - minValue
     - Int/Double/Float
     - The set lower limit of the threshold.
   * - maxValue
     - Int/Double/Float
     - The set upper limit of the threshold.
   * - enableMinJudger
     - Boolean
     - Whether minimum value juder is enabled.
   * - enableMaxJudger
     - Boolean
     - Whether maximum value juder is enabled.


### Output Example

.. image:: media/minmax_outlier_result.png

<!--end-->
