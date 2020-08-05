# Connecting with IDEA through JDBC

<br />

The Data Federation service enables the reading of data from data sources through the JDBC interface in IDEA.

<br />

This section shows how to connect data sources in IDEA through the JDBC interface.


## Prerequisites

- You have installed IDEA Ultimate edition.
- You have created a data federation channel and authorized an application to access data through the channel.

## Configuration Steps

1. From the channel list on the **Channel Manager** page, find the target channel, select **... > Get URL**, and copy the JDBC URL of the channel. 

2. Run IDEA and download the data federation JDBC jar package from the maven repository to your local repository. The maven dependency is as per the below.

   ```
   <groupId>com.envisioniot</groupId>
   <artifactId>enos-datafederation-jdbc</artifactId>
   <version>0.0.1</version>
   ```

   <br />

3. On the **Database** page, click **+** on the toolbar, and select **Driver and Data Source** to create a driver.

   .. image:: ../../media/idea_jdbc.png

   <br />

4. Enter the driver name, class name, and select the downloaded jar package in the **Driver files** section.

   .. image:: ../../media/idea_jdbc_driver.png

   <br />

5. On the **Database** page, click **+** on the toolbar, and select **Data Source** to create the data source.

6. Enter the data source name and complete the following configuration under the **General** tab.

   - **User**: Enter the access key of the application that is authorized by the data federation channel.
   - **Password**: Enter the secret key of the application. For information about getting the application access key and secret key, see [Registering and Managing Applications](/docs/app-development/en/dev/app_management/managing_apps.html).
   - **URL**: Enter the JDBC URL that was copied in step 1 and append the ``dbEscapeNeeded=true`` parameter at the end of the JDBC URL. For example, `jdbc:datafederation://{domain_name}/data-federation/v2.0/channels/read/{channel_id}?orgId={orgId}&dbEscapeNeeded=true`.
   - **Driver**: Select the created driver in steps 2 and 3.

   <br />

   .. image:: ../../media/idea_jdbc_setting.png

   <br />

7. Click **Test Connection** to test the configuration. Click **OK** next to view the Catalog information (the schemas cannot be viewed).

   .. image:: ../../media/idea_jdbc_connected.png

   <br />

8. Right-click on the Catalog, select **Database Tools > Manage Shown Schemas**, and then choose **All schemas** to display all the schemas.

   .. image:: ../../media/idea_jdbc_all_schemas.png

   <br />

9. View the schemas of the connected data source and then choose to load data from the data source or transform the data as needed.

   .. image:: ../../media/idea_jdbc_result.png



<!--end-->
