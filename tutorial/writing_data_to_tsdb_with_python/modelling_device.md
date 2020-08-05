# Unit 1: Modelling the Computer Device

In this Unit, registering a model, product, and device for the Computer.

## Creating a Model

Create a model for Computer and define the following measurement points for the model (you can also reuse an existing model):

<br />

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Feature Type
     - Name   
     - Identifier   
     - Point Type
     - Description   
   * - Measurement Points
     - mem_used
     - mem_used
     - AI
     - Computer memory usage data
   * - Measurement Points
     - cpu_used
     - cpu_used
     - AI
     - Computer CPU usage data

<br />

See the following example:

.. image:: media/measurement_points.png

.. note:: The model ID will be required in the Python script for writing data to TSDB.

## Creating a Product

Create a product for Computer under the created model.

<br />

See the following example:

.. image:: media/computer_product.png


## Creating a Device

Create an asset device for the computer under the created product.

<br />

See the following example:

.. image:: media/computer_device.png

.. note:: The asset ID of the device will be required in the Python script for writing data to TSDB.


## Next Unit

[Configuring Storage Policy for Measurement Points](configuring_storage_policy)
