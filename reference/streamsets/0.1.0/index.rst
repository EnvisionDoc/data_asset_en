Calculator Library 0.1.0 Documentation
=============================================

The Streaming Calculator Library 0.1.0 includes operators for asset information query, data aggregation, exception interpolation, event-time-based time window aggregation, and threshold filtering.

Origin
----------------------------------

.. toctree::
   :maxdepth: 1

   dev_raw_data_source


Asset Data Querying Operators
---------------------------------------

.. toctree::
   :maxdepth: 1

   tsl_asset_lookup
   tsl_child_asset_lookup
   tsl_parent_asset_lookup
   tsl_point_lookup


Data Processing Operators
-----------------------------------

.. toctree::
   :maxdepth: 1

   point_selector
   record_generator
   partitioner
   record_sorter_by_time
   fixed_time_window_aggregator
   sliding_time_window_aggregator
   batch_merger
   last_changed_record_appender
   latest_record_merger
   record_capturer
   record_restorer


Advanced Data Processors

.. toctree::
   :maxdepth: 1

   python_evaluator
   java_script
   internal_http_client


Data Quality Tagging Operators
--------------------------------------

.. toctree::
   :maxdepth: 1

   late_point_tagger
   off_limit_tagger


Electric Energy Calculating Operators
--------------------------------------------

.. toctree::
   :maxdepth: 1

   last_record_appender
   cumulant_decomposer
   simplified_time_window_aggregator


Destination
-----------------------------------

.. toctree::
   :maxdepth: 1

   trash


﻿Calculator Performance Description
------------------------------------

.. toctree::
   :maxdepth: 1

   performance
