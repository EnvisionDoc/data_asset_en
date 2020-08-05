# Registering an Amazon S3 Data Source

<br />

Before synchronizing data from an external Amazon S3 database for analysis, you need to register the data source to specify the cloud region where the database sits in AWS, the credentials to use to access the S3 database, and other information about the data source.

<br />

This section shows the steps to register an Amazon S3 data source in EnOS.

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

   - **Data Source Type**: Select S3.
   - **Region**: Select the cloud region of the S3 database.
   - **Access Key ID**: Enter the access key ID of the S3 database.
   - **Secret Access Key**: Enter the access key to use to sign the requests sent to the S3 database.
   - **Data Source Description**: Enter a description for the data source.

   <br />

4. Click **Test** to test the data source connection.

5. Click **OK** to save the configuration.


## Results

The data source will be shown in the **Data Source Registration** table.

## Next Step

When the connection is successfully established, you can follow the steps below to synchronize data from the data source to EnOS Hive.

1. Create a Hive table to store the retrieved data. For more information, see [Creating a Hive Table](/docs/data-asset/en/dev/howto/data_ide/data_explorer/creating_hivetable.html).

2. Configure a data synchronization job to synchronize data from the data source to the target Hive table. For more information, see [Data Synchronization](../data_integration/index).
