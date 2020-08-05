# Registering an Azure Blob Data Source

<br />

Before synchronizing files from an external Azure Blob database to EnOS HDFS, or using the Data Archiving service to store archive files in the Azure Blob database, you need to register the data source to specify the cloud region where the database sits in Azure, the storage account and password to access the Blob database, and other information about the data source.

<br />

This sections shows the steps to register an Azure Blob data source in EnOS.

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

   - **Data Source Type**: Select BLOB.
   - **Storage Domain**: Select a storage domain.
   - **Account Name**: Enter the storage account to access the Blob database.
   - **Account Key**: Enter the account key of the storage account.
   - **Data Source Description**: Enter a description for the data source.

   <br />

4. Click **Test** to test the data source connection.

5. Click **OK** to save the configuration.


## Results

The data source will be shown in the **Data Source Registration** table.

## Next Step

When the connection is successfully established, you can configure a data synchronization job to synchronize files from the external Blob database to EnOS HDFS. For more information, see [Data Synchronization](../data_integration/index).

<br />

You can also configure a data archiving job to archive asset data and store the archive files in the target Blob database. For more information, see [Configuring Data Archiving Jobs](../archive/configuring_archive_storage.html).
