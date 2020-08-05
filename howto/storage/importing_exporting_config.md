# Importing and Exporting Storage Policy Configuration

.. note:: This feature is available for the EnOS 2.1 Update and newer releases.

<br />

When you need to migrate TSDB storage policy configuration across environment or across OUs, you can export the existing configuration of storage policy groups or measurement points and import it into the new environment or OU for rapid configuration and deployment.

<br />

The storage policy configuration files can be generated or retrieved by the following methods.

- If your OU already has storage policy groups and storage policy configuration, you can export the configuration and save it as an Excel file. Update the file as needed and then import the configuration file in the new environment or OU to create a storage policy group quickly.

- Download the configuration file template, edit the file with storage policy configuration, and import the file to create a storage policy group quickly.

- If your OU already has storage policy groups and storage policy configuration, you can download the storage configuration of measurement points for each storage type and save it as an Excel file. Update the file as needed and then upload the configuration file to update the storage policy configuration quickly.


## Exporting Storage Policy Group Configuration

1. Log in to the **EnOS Management Console** and select **Time Series Data Management > Storage Policy**.

2. View the basic information and configuration of the existing storage policy group, click **... More** in the **Group Configuration** section, and select **Export Group**. The configuration file will be exported and saved as a file named ``enos_tsdb_storage_policy_{group_name}.xlsx``.

   .. image:: ../../media/export_storage_group.png

   <br />

3. Open the downloaded configuration file, update the storage policy configuration in the file as needed.

   - **policy** sheet: Editing models, measurement points, and corresponding data types

   - **retention** sheet: Editing the storage time of each storage type

   <br />

4. Save the configuration file, which can be imported to the system for creating a storage policy group with configured storage policy quickly.


## Importing Storage Policy Group Configuration

Follow the steps below to create a storage policy group and complete storage policy configuration by importing a storage policy configuration file.

1. Log in to the **EnOS Management Console** and select **Time Series Data Management > Storage Policy**.

2. Click the **+** icon in the upper right corner of the page and select **Import Group**.

3. Enter a name for the storage policy group.

4. If you need to use the storage policy configuration template, click **Download Policy Template**. If you already have a storage policy configuration file ready, click **Upload Policy Template**, navigate and select the configuration file.

   .. image:: ../../media/import_storage_policy_group_1.png

   <br />

5. Click **OK**, and system will check the validity of the storage policy configuration file. After validation, the storage policy group will be created.


## Verifying the Imported Storage Policy Group Configuration

When the storage policy group is created, follow the steps below to verify the configuration.

1. Check if the storage policy for models and measurement points is completely configured, and if the configuration meets your business requirement.

2. Check if the storage time for measurement points is correct, and if the configuration meets your business requirement.

3. If you need to update the configuration, click the **Edit** icon and make changes as needed.


## Downloading and Uploading Measurement Point Storage Configuration

If your OU already has storage policy groups and storage policy configuration, you can download the storage configuration of measurement points for each storage type and save it as an Excel file. Update the file as needed and then upload the configuration file to update the storage policy configuration quickly.

1. Log in to the **EnOS Management Console**, select **Time Series Data Management > Storage Policy**, and select the created storage policy group.

2. Under the storage policy group, click the **Edit** icon of the target storage type to open the **Edit Storage Policy** page.

3. Click **Download Point Storage Configuration** to save the configuration file of the storage type locally.

   .. image:: ../../media/downloading_point_storage_policy.png

4. Edit the configuration file as needed, click **Upload Point Storage Configuration**, navigate and upload the updated configuration file.

5. The system will check the validity of the storage policy configuration file. After validation, click **OK** to save the measurement point storage configuration.

<!--end-->
