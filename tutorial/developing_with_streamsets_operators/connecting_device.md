# Unit 3: Connecting Wind Turbine Devices to EnOS

<br />

After the wind turbine devices are created and the data storage policy is configured based on the created models, we can start to connect the wind turbine devices to EnOS and upload the wind turbine energy production data to the cloud.

<br />

In this unit, we will use the **Device Simulator** in the **EnOS Management Console** to simulate the energy production meter reading data of the wind turbines.  

## Adding a Device Simulator

1. Select **Asset Management > Simulator**.

2. Click **New Simulator**, and select the wind turbine devices to be simulated.

   .. image:: media/adding_simulator.png

   <br />

3. Click **OK** to create a simulator for the selected devices. In the list of simulators, you can see the wind turbine devices to be provisioned.

   .. image:: media/added_simulator.png


## Defining the Simulation Data Sample

1. Click **Batch Define Sample** .

2. From the **Product** field, select the **product_eos_turbine** product.

3. Click **Download** to download the data sample template.

4. Edit the *sample.xlsx* file with the wind turbine energy production meter reading data sample.

   .. image:: media/sample_data.png

   <br />

5. Click **Upload** to select the data sample file to be uploaded, and click **Next**.

   .. image:: media/defining_data_sample.png
    :width: 400px 

   <br />

6. Select the wind turbine devices that need data simulating and click **Confirm**.

   .. image:: media/selecting_simulated_devices.png
    :width: 400px 

<br />

The simulated wind turbine devices are now ready to be started.


## Starting the Device Simulators

1. Select the device simulators to be started from the list.

2. Click **More > Batch Start**.

3. Set an end time for all the selected simulators and click **OK**. The status of the device simulators will be changed to *Simulating*.

   .. image:: media/simulated_devices.png

   <br />

4. The status of the wind turbine devices on the **Device Asset** page should be *Online* now.

   .. image:: media/device_status.png


## Next Unit

[Developing a Stream Data Processing Job](developing_streams)

<!--end-->
