# Unit 1. Registering Data Source

<br />

The first step of synchronizing data to EnOS Hive is to register the external data sources through Data Source Registration.

<br />

In this unit, configure the connection to the MySQL server that hosts the employee data to be synchronized to EnOS Hive.

1. In the **EnOS Management Console**, click **Data Source Registration** from the left navigation panel.

2. On the **Data Source Registration** page, click the **Add Data Source** button.

3. In the **Data Sources** window, provide the following information:

   - **Data Source**: Name of the data source.
   - **Data Source Type**: Select **MYSQL** from the drop-down list.
   - **Host Name or IP Address**: Host name or IP address of the MySQL server.
   - **Database Name**: Enter a unique name for the database to be connected.
   - **Port**: Port of the MySQL server.
   - **Username**: User name for accessing the database.
   - **Password**: Password of the user name.
   - **Data Source Description**: Short description of the data source.

   <br />

4. Click **OK** to save the configuration. See the following data source sample:

   .. image:: media/data_connection.png

After the data source is registered, the data source item is shown in the **Data Source Registration** table.

## Next Unit

[Creating a Target Hive Table](creating_hive_table)
