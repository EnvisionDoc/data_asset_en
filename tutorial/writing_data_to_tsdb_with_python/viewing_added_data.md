# Unit 4: Viewing Measurement Point Data

When the workflow with Python task node runs successfully to write measurement point data in TSDB, you can verify the added data with the Data Insights feature of Time Series Data Management.

1. Log in to the EnOS Management Console, select Time Series Data Management > Data Insights, and configure the data filtering conditions.

2. In the **Select Time Range** section, select **1D**。

3. Click the **Select Devices** input box, enter the asset ID of the computer device, and select the device from the drop-down list.

   .. image:: media/data_insights.png

4. In the **Selected Measuring Points** column, click on the device name, expand the list of measurement points, and select the ``mem_used`` and ``cpu_used`` measurement points.

5. View the queried measurement point data, including the latest data of the selected measurement points and the last updated time of the data.

   .. image:: media/viewing_queried_data.png


<!--end-->
