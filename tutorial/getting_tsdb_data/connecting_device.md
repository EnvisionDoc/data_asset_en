# Unit 3: Registering and Connecting the Device to EnOS

<br />

After your device model is created and the data storage policy is configured based on the device model, you can register the electric meter in the EnOS Management Console and perform device-end development so that the device can connect to EnOS Cloud and start to transmit data.

## Create a Product for the Electric Meter

Create a product with the basic settings below.

- **Product Name**: SmartElectricMeter
- **Asset Type**: Device
- **Model**: ElectricMeter
- **Data Type**: Json
- **Certificate-Based Authentication**: Disabled
- **Description**: Smart Electric Meter

## Register the Electric Meter Device

Create a smart electric meter device with the basic settings below.

- **Product**: SmartElectricMeter
- **Device Name**: Meter01
- **Device Key**: Optional (it can be generated automatically by the system)
- **Time Zone/City**: UTC+08:00
- **Use DST**: No

## Perform Device-end Development and Initialize Connection

The [Connecting a Simulated Device to EnOS](/docs/device-connection/en/dev/tutorial/connecting_device_simulated/index.html) tutorial shows the steps for how to perform device-end development. You can follow the same steps to connect the smart electric meter to EnOS for this tutorial.

## Next Unit

[Developing Stream Data Processing Jobs](developing_streams)

<!--end-->
