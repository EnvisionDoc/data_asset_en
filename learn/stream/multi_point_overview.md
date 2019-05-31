# Multi Point Merge Template

In IoT business scenarios, the data of a measuring point might be calculated from the data of other measuring points of the same device. For example, *point_C = point_A + point_B*. In which, *point_A* and *point_B* are measuring points for ingesting asset raw data. EnOS Streaming Analytics provides a Multi Point Merge template to enable data calculation among multiple measuring points of the same device.

## Features

1. Supporting calculation among multiple measuring points of the same device.

2. Strong syntax for calculation expressions.

3. Data processing triggered by the data arrival of a measuring point.

4. Supporting timing interpolation strategy (if the data of a measuring point does not arrive when calculation starts, the latest data of the measuring point will be used for calculation).

5. Supporting associated calculation with master data

## Data Sources

The data involved in the calculation must belong to the same device model. The variables in the calculation expression can be measuring points and attributes of the model. When writing the data processing expression, you must use measuring points and attributes that have been declared as data sources. The conditions for configuring data sources are as follows:

- Multiple models are supported
- Multiple measuring points and attributes in a model are supported

## Triggering Mode

The Multi Point Merge template currently supports triggering data processing by a measuring point.

When designing a data processing strategy record, you need to select a measuring point as the triggering point. Each time when the data of this measuring point arrives, the data processing task will be triggered. The data timestamp of the triggering point will be used as the timestamp of the output record.

If the data of a measuring point does not arrive when a data processing task is triggered, the latest data record of the measuring point will be used for calculation.   

## Data Processing Strategy

The configuration of a data processing strategy record is as follows:

**Output Point**: The measuring point that receives the output value of the data processing expression. Supported data types include int, float, string, and bool (other types will be converted to string).

**Output Logic**: The data processing expression. For supported syntax of the expression, see [Multi Point Merge Expression Syntax](statement_syntax).

**Triggering Point**: The measuring point that triggers the data processing strategy. The triggering point, output point, and the measuring points and attributes used in the data processing expression must belong to the same model. The triggering point cannot be the output point.
