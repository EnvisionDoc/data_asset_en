StreamSets Operator Reference
=========================

.. contents::
   :depth: 1
   :hidden:

EnOS Stream Analytics provides a set of underlying packaged StreamSets operators, supporting asset main data query, window aggregation, data filtering and interpolation, and electric energy calculation. Data engineers and application developers can use these StreamSets operators to design customized stream data processing jobs to meet the requirements of complex business scenarios.

Asset Data Querying Operators
-------------------------------------
.. toctree::
   :maxdepth: 1

   tsl_asset_lookup
   tsl_child_asset_lookup
   tsl_parent_asset_lookup
   tsl_point_lookup
   site_lookup
   

Data Processing Operators
-----------------------------------
.. toctree::
   :maxdepth: 1

   point_selector
   asset_generator
   partitioner
   asset_partitioner
   point_partitioner
   time_sort
   window_aggregator
   fixed_batch_pivotor
   earliest_change_record_appender
   state_capturer
   state_restorer

Advanced Data Processors

.. toctree::
   :maxdepth: 1

   python_evaluator
   http_lookup

Data Quality Tagging Operators
---------------------------------------
.. toctree::
   :maxdepth: 1

   late_point_filter
   min_max_outlier

Electric Energy Calculating Operators
--------------------------------------------
.. toctree::
   :maxdepth: 1

   last_record_appender
   delta_calculator
   delta_down_sampler
