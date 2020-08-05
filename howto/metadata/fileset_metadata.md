# Querying Fileset Metadata

<br />

With Data Asset Catalog, you can create a fileset and query the metadata information of filesets in the OU, including the basic information, file list, and file header.

## Creating a Fileset

1. Log in to the **EnOS Management Console** and select **Data Asset Catalog** from the left navigation menu.
2. From the **New** drop-down menu on the left, select **Fileset**.
3. On the **New Fileset** page, enter the ID and name of the fileset to be created.
4. From the **File Type** drop-down list, select the type of file in the fileset.
5. Click **Add Fileset Pattern** and complete the following configuration.
     - **Source Type**: Select the storage source of files. Options are HDFS, S3, and Blob.
     - **Storage Source**: Select the corresponding data source that is registered through Data Source Registration.
     - **Pattern**: Enter the fileset pattern. For example: `${base_dir}/${device_type}/${site_local_date}/${site_id}_${xxx}.csv`
6. Repeat step 5 to add another fileset pattern (at most 2 fileset pattern entries are supported).
7. Enter a description of the fileset.
8. Click **Confirm** to save the fileset configuration.

.. image:: media/new_fileset.png

## Querying Filesets

The Data Asset Cataloge enables you to query the metadata of all filesets in the OU. You can search for a fileset with the following steps.

1. Under the **Type** list on the left side of the **Data Asset Catalog** page, select **Fileset**.

2. In the search field, type the keywords to search for filesets.

   .. image:: media/fileset_search_result.png

.. note:: The search keywords are case sensitive and can match the ID, name, and description of filesets.

## Viewing, Editing, and Deleting Filesets

In the fileset search results, click the **View** icon to open and view the metadata of the fileset at the fileset details page.

### Basic Information

Under the **Basic** tab, you can view the basic information of the fileset, such as:

- The fileset ID, name, and description.
- The file type.
- The file pattern, including the data source name and the complete file pattern.
- The person who created the fileset, and the time when the fileset was created and updated.

<br />

To attach tags to the fileset, click **Attach Tags** and select the pre-defined tag template in the pop-up window. Click the **Edit** or **Delete** icon to edit or delete tags that are attached to the fileset.

<br />

Click **Edit Fileset** to update the name, description, and file type, and add or remove fileset patterns.

<br />

Click **Delete Fileset** to delete the fileset. Note that deleted filesets cannot be restored.


.. image:: media/fileset_basic_info.png


<!--end-->