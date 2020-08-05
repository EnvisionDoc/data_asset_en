# Unit 2: Configuring Storage Policy for Measurement Points

Before writing measurement point data to TSDB, you need to configure TSDB storage policy for the measurement points.

## Prerequisites

Your OU has created a storage policy group with the **Computer** model associated. Otherwise, you need to create a storage policy group first. For more information, see [Creating a TSDB Storage Policy Group](../../howto/storage/creating_storage_group.html).

<br />

In this unit, configure storage policy for the following measurement points that have been defined when creating the Computer model.

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Measurement Point
     - Storage Type  
     - Description   
   * - mem_used
     - AI Raw Data
     - Adding extra data of the computer memory usage to TSDB, stored as AI raw data.
   * - cpu_used
     - AI Raw Data
     - Adding extra data of the computer CPU usage to TSDB, stored as AI raw data.

<br />

See the following example:

.. image:: media/storage_policy.png

<br />

For more information about configuring storage policy for measurement points, see [Configuring TSDB Storage](../../configuring_tsdb_storage).


## Next Unit

[Developing a Batch Processing Workflow](developing_workflow)

<!--end-->
