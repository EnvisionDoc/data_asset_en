# Connecting with Power BI through OData

<br />

The Data Federation service enables the reading of data from data sources through the OData interface in Excel and Power BI.

<br />

This section shows how to connect data sources in Power BI through the OData interface.

## Prerequisites

- You have installed Power BI.
- You have created a data federation channel and authorized an application to access data through the channel.

## Configuration Steps

1. From the channel list on the **Channel Manager** page, find the target channel, select **... > Get URL**, and copy the OData URL of the channel.

   .. image:: ../../media/copy_channel_url.png

   <br />

2. Run Power BI on your workstation and select **Home > Get Data > OData feed** from the menu.

   .. image:: ../../media/powerbi_odata.png

   <br />

3. In the pop-up window, select **Basic**, enter the OData URL that was copied in step 1 in the **URL** field, and click **OK**.

   .. image:: ../../media/powerbi_enter_odata_url.png

   <br />

4. In the **OData feed** window, select **Basic**, and complete the following.

   - **User name**: Enter the access key of the application that is authorized by the data federation channel.
   - **Password**: Enter the secret key of the application. For information about getting the application access key and secret key, see [Registering and Managing Applications](/docs/app-development/en/dev/app_management/managing_apps.html).
   - **Select which level to apply these settings to**: Select the complete URL level, for example: `{domain_name}/data-query-proxy/channels/read/{channel_id}/odata.svc`.

   <br />

   .. image:: ../../media/powerbi_odata_setting.png

   <br />

5. Click **Connect**, and the metadata of the data source will be displayed. You can then choose to load data from the data source to Power BI or transform the data as needed.

   .. image:: ../../media/powerbi_odata_result.png


<!--end-->
