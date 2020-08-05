# Creating a Channel

<br />

Before using the Data Federation service to read data from and write data to data storage systems, you need to create a read channel or write channel.

## Prerequisites

- You are able to access the Data Federation module.
- Your OU has requested for the **Data Federation** resource.
- You have registered the data source types that you need through **Data Source Registration**.

## Creating a Channel

1. Log in to the **EnOS Management Console** and click **Data Federation > Channel Manager**. If your OU has not requested for the Data Federation resource, go to the **Resource Management** page. If your OU has not registered the required data sources, go to the **Data Source Registration** page.

2. Click **New Channel**, enter the channel name, select the channel type, enter a short description about the channel, and click **OK** to open the channel configuration page.

3. At the **Data Source** section, click **+ Add** to configure the data source information in the pop-up window.

   - **Type**: Select the data source type from the drop-down list.
   - **Data Source**: Select the registered data source from the drop-down list.
   - **Alias**: Set the alias for the selected data source. Once submitted, the data source alias cannot be changed.

   .. image:: ../../media/data_federation_source.png

   <br />

4. Repeat step 3 to add more data sources (a single data source can be added only once, and the data source alias must be unique in the OU).

5. Select the requested data federation resource for the channel. A channel can only use 1 resource. If the requested resource does not meet the requirement, request for more quota through the **Resource Management** page.

   .. image:: ../../media/data_federation_submit.png

   <br />

6. When the above configuration is completed, click **OK** to submit the channel configuration. Once submitted, the channel will be started automatically to obtain access to the specified data sources.


## Retrieving the Channel URL

When the channel is running normally, you can get the URL of the channel with the steps below.

1. From the list of channels, find the running channel, and select **... > Get URL**.

   .. image:: ../../media/data_federation_url.png

   <br />

2. In the pop-up window, copy the generic URL, JDBC URL, or OData URL, which can be used for accessing the data separately. For more information about accessing data through OData, see [Reading and Writing Data](reading_writing_data).


<!--end-->
