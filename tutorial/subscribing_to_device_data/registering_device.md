# Unit 1: Registering the Device on EnOS Management Console

<br />

Before connecting a smart electric meter to EnOS IoT Hub, you need to register the electric meter on the EnOS Management Console, which includes defining the electric meter model, creating a meter product, and registering a meter device.

<br />

The [Connecting a Simulated Device to EnOS](/docs/device-connection/en/dev/tutorial/connecting_device_simulated/index) tutorial shows the detailed steps for registering a device on EnOS Management Console. You can follow the same steps to register a smart electric meter with the following information.

## Creating a Model

Create a model with the basic settings below.

<br />

- **Identifier**: Grid.TopupAcMeter
- **Model Name**: Grid.TopupAcMeter
- **Category**: Grid
- **Create From**: No
- **Source Model**: NA
- **Description**: AC meter that has a temperature sensor

<br />

Define the "Temperature" measurement point for the model.

<br />

.. list-table::
   :widths: auto
   :header-rows: 1

   * - Feature Type
     - Name   
     - Identifier   
     - Point Type
     - Data Type   
   * - Measurement Point
     - Temperature
     - Temperature
     - AI
     - double

## Creating a Product

Create a product with the basic settings below.

<br />

- **Product Name**: Grid.PrepaidElectricityMeter
- **Asset Type**: Device
- **Model**: Grid.TopupAcMeter
- **Data Type**: Json
- **Certificate-based bi-directional authentication**: Disabled
- **Description**: State grid standard electricity meter

## Creating a Device

Create a smart electric meter with the basic settings below.

<br />

- **Product**: Grid.PrepaidElectricityMeter
- **Device Name**: Demo_meter
- **Use DST**: Disable
- **timezone**: UTC+08:00
- **Device Key**: Optional (it can be generated automatically by the system)


## Next Unit

[Simulating Device Data and Configuring Alert Settings](setting_alerts)
