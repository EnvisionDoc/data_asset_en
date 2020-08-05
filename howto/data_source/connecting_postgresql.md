# Registering a PostgreSQL Data Source

<br />

Before synchronizing data from EnOS Hive to an external PostgreSQL database, you need to register the data source to configure the information of the data connection and the connection to the source database.

<br />

This section shows the steps to register a PostgreSQL data source in EnOS.

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

   - **Data Source Type**: Select PostgreSQL.   
   - **Host Name or IP Address**: Enter the host name or IP address where the database is hosted.
   - **Database Name**: Enter the name that uniquely identifies the database.
   - **Port**: Enter the port to access the database. EnOS will use the address, database name, and port to establish the JDBC connection from EnOS to the database.
   - **Username**: Enter the user name for accessing the database.
   - **Password**: Enter the password of the user name.
   - **Data Source Description**: Enter a description for the data source.

   <br />

4. Click **Test** to test the data source connection.

   <!-- .. image:: ../media/postgresql_connection.png
      :width: 400px -->

5. Click **OK** to save the configuration.


## Results

The data source will be shown in the **Data Source Registration** table.

## Next Step

When the connection is successfully established, you can configure a data synchronization job to synchronize data from EnOS Hive to the target PostgreSQL database. For more information, see [Data Synchronization](../data_integration/index).
