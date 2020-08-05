# Unit 1: Registering and Connecting Wind Turbines to EnOS Cloud

<br />

In this unit, we will first create the models, products, devices, and device trees for the wind turbine and wind farm.

## Creating a Model for Wind Turbines

1. Create a model for wind turbines with the basic settings below.
   - **Identifier**: eos_turbine
   - **Model Name**: eos_turbine
   - **Category**: N/A
   - **Created From**: No
   - **Source Model**: No
   - **Description**: Model for wind turbines

   <br />

2. Define the following measurement points for the **eos_turbine** model.

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Feature Type
     - Name   
     - Identifier   
     - Point Type
     - Description   
   * - Measurement Point
     - ammeter
     - ammeter
     - AI
     - The meter reading data of the energy production.
   * - Measurement Point
     - production_daily
     - production_daily
     - PI
     - The daily energy production data of the wind turbine.

## Creating a Model for Wind Farms

1. Create a model for wind farms with the basic settings below.
   - **Identifier**: eos_site
   - **Model Name**: eos_site
   - **Category**: N/A
   - **Created From**: No
   - **Source Model**: No
   - **Description**: Model for wind farms

   <br />

2. Define the following attribute for the **eos_site** model.

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Feature Type
     - Name   
     - Identifier   
     - Data Type
     - Default Value
     - Description
   * - Attributes
     - carbon.reduction.param
     - carbon.reduction.param
     - double
     - 0.997
     - The parameter for calculating the carbon reduction data of the wind farm.

<br />

<span>3</span>. Define the following measurement points for the **eos_site** model.

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Feature Type
     - Name   
     - Identifier   
     - Point Type
     - Description
   * - Measurement Point
     - carbon.reduction
     - carbon.reduction
     - AI
     - The calculated carbon reduction data of the wind farm.
   * - Measurement Point
     - carbon.reduction.daily
     - carbon.reduction.daily
     - AI
     - The calculated daily carbon reduction data of the wind farm.
   * - Measurement Point
     - production_day
     - production_day
     - PI
     - The daily energy production data of the wind farm.

<br />

Example of the created models:

.. image:: media/created_models.png


## Creating Products

1. Create a product for wind turbines with the basic settings below.
   - **Product Name**: product_eos_turbine
   - **Asset Type**: Device
   - **Model**: eos_turbine
   - **Data Type**: JSON
   - **Certificate-Based Authentication**: Disabled
   - **Description**: Wind turbine product

   <br />

2. Create a product for wind farms with the basic settings below.
   - **Product Name**: product_eos_site
   - **Asset Type**: Device
   - **Model**: eos_site
   - **Data Type**: JSON
   - **Certificate-Based Authentication**: Disabled
   - **Description**: Wind farm product

   <br />

Example of the created products:

.. image:: media/created_products.png

## Creating Devices

Create 5 wind turbine devices (different device names) with the basic settings below.

- **Product**: product_eos_turbine
- **Device Name**:  1101, 1102, 1103, 2201, 2202
- **Time Zone/City**: UTC+08:00
- **Use DST**: No
- **Device Key**: Generated automatically by the system

Example of the created devices:

.. image:: media/created_devices.png



## Creating an Asset Tree

1. Create an asset tree for the 2 wind farms and 5 wind turbine devices with the basic settings below.

   - **Name**: eos_tree
   - **Asset Tree Tag**: `eos_tree:true`
   - **Model**: None
   - **Time Zone/City**: UTC+08:00

   <br />

   .. image:: media/created_asset_tree.png

   <br />

2. Add the following sub-nodes (sites) to the created asset tree.

   - **Name**: site_01, site_02
   - **Model**: eos_site
   - **Time Zone/City**: UTC+08:00

   <br />

   .. image:: media/asset_tree_node.png

   <br />

3. Add the following sub-nodes (wind turbine devices) to the created site.

   - **Name**: 1101, 1102, 1103
   - **Model**: eos_turbine
   - **Time Zone/City**: UTC+08:00
   - **Asset Type**: Device Asset

   <br />

   .. image:: media/configured_asset_tree.png



## Next Unit

[Configuring Storage Policy for the Original and Calculated Data](configuring_storage_policy)
