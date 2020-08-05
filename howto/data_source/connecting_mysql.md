# Registering a MySQL or SQL Server Data Source

<br />

Before synchronizing data from an external MySQL or SQL Server database for analysis or synchronizing data from EnOS Hive to an external MySQL database, you need to register the data source to specify the data connection and the JDBC connection information to the source database.

<br />

This section shows the steps to register a MySQL or SQL Server data source in EnOS.

## Procedure

1. In the **EnOS Management Console**, click **Data Source Registration** from the left navigation menu.

2. Click **Add Data Source**.

3. In the **Data Sources** window, provide information for the following.

   - **Data Source**: Enter a name for the data source. The maximum length is 50 characters and can be a combination of the following characters.
     - a through z
     - A through Z
     - 0 through 9
     - _ (underscore) 

     <br />

   - **Data Source Type**: Select MYSQL or SQL Server   
   - **Host Name or IP Address**: Enter the host name or IP address where the database is hosted.
   - **Database Name**: Enter the name that uniquely identifies the database.
   - **Port**: Enter the port to access the database. EnOS will use the address, database name, and port to establish the JDBC connection from EnOS to the database.
   - **Username**: Enter the user name for accessing the database.
   - **Password**: Enter the password of the user name.
   - **Data Source Description**: Enter a description for the data source.

   <br />

4. Click **Test** to test the data source connection.

5. Click **OK** to save the configuration.


## Results

The data source will be shown in the **Data Source Registration** table.

## Next Step

When the connection is successfully established, you can follow the steps below to synchronize data from the external data source to EnOS Hive or from EnOS Hive to the external MySQL database.

1. Create a Hive table to store the retrieved data. For more information, see [Creating a Hive Table](/docs/data-asset/en/dev/howto/data_ide/data_explorer/creating_hivetable.html).

2. Configure a data synchronization job to synchronize data from the external data source to EnOS Hive or from EnOS Hive to the external MySQL database. For more information, see [Data Synchronization](../data_integration/index).
