# Calculator Performance Description

<br />

.. note:: Because of dependency on external interfaces and different user business logic, the following performance data of calculators is for reference only.

<br />

With the same resource configuration, the calculating performance of each calculator is shown in the following table.

## Resource Configuration

.. list-table::
   :widths: 40 60
   :header-rows: 1

   * - Configuration
     - Description
   * - Resource Configuration
     - 2Core, 4GB

## Calculator Performance

.. list-table::
   :widths: 50 50
   :header-rows: 1

   * - Calculator
     - Calculation Capacity (record/s)
   * - TSL Asset Lookup
     - 11500
   * - TSL Child Asset Lookup
     - 12700
   * - TSL Parent Asset Lookup
     - 10600
   * - TSL Point Lookup
     - 12000
   * - Point Selector
     - 16200
   * - Record Generator
     - 20000
   * - Partitioner
     - 5600
   * - Record Sorter By Time
     - 17000
   * - Fixed Time Window Aggregator
     - 6500
   * - Sliding Time Window Aggregator
     - 6600
   * - Batch Merger
     - 16200
   * - Last Changed Record Appender
     - 6300
   * - Latest Record Merger
     - 10100
   * - Record Capturer
     - 13000
   * - Record Restorer
     - 13000
   * - Python Evaluator
     - 10300
   * - JavaScript
     - 12100
   * - Late Point Tagger
     - 12300
   * - Off Limit Tagger
     - 8700
   * - Last Record Appender
     - 6300
   * - Cumulant Decomposer
     - 6100
   * - Simplified Time Window Aggregator
     - 20000




<!--end-->
