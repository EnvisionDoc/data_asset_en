# Registering a Redis Data Source

<br />

To synchronize data from a Redis database for analysis, you need to register the data source and configure the data connection to the source database.

<br />

This section shows the steps to register a Redis data source in EnOS.


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

   - **Data Source Type**: Select REDIS.   
   - **Host Name or IP Address**: Enter the host name or IP address of the Redis instance. For cluster environment, click **Add Server Address** to add more Redis instances.  
   - **Password**: Enter the password for accessing the Redis instance.
   - **Data Source Description**: Enter a description for the data source.

   <br />

4. Click **Test** to test the data source connection.

   <!-- >.. image:: ../media/redis_connection.png
      :width: 400px -->

5. Click **OK** to save the configuration.


## Results

The data source will be shown in the **Data Source Registration** table.
