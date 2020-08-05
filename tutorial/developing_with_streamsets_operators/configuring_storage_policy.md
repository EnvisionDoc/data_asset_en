# Unit 2: Configuring Storage Policy for the Original and Calculated Data

<br />

To store the energy production data of the wind turbines and the calculated daily energy production data of the wind farms, we need to configure the data storage policy. Otherwise, the uploaded and calculated data will not be stored in TSDB.

<br />

In this unit, we will configure the storage policy for the following measurement points that were defined when creating the **eos_turbine** and **eos_site** models.

.. list-table::
   :widths: 20 20 60
   :header-rows: 1

   * - Measurement Point
     - Storage Type
     - Description
   * - eos_turbine::ammeter
     - AI Raw Data
     - When the energy production data of a wind turbine is uploaded, store the raw data of the *ammeter* measurement point in TSDB directly.
   * - eos_site::carbon.reduction
     - AI Raw Data
     - Get the carbon reduction data of a wind farm with a stream processing job, and then store the calculated data in TSDB.
   * - eos_site::carbon.reduction.daily
     - AI Raw Data
     - Get the daily carbon reduction data of a wind farm with a stream processing job, and then store the calculated data in TSDB.
   * - eos_turbine::production_daily
     - PI Data
     - Get the daily energy production data of a wind turbine with a stream processing job, and then store the calculated data in TSDB.
   * - eos_site::production_day
     - PI Data
     - Get the daily energy production data of a wind farm with a stream processing job, and then store the calculated data in TSDB.

<br />

The figure below shows the configured storage policy for the AI Raw Data storage type.

.. image:: media/storage_policy_ai.png

<br />

The figure below shows the configured storage policy for the PI Data storage type.

.. image:: media/storage_policy_pi.png

For the detailed steps for configuring storage policies, see [Configuring TSDB Storage](../../configuring_tsdb_storage).


## Next Unit

[Connecting Wind Turbine Devices to EnOS](connecting_device)

<!--end-->
