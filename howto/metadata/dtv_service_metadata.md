# Querying DTV Service Metadata

<br />

With Data Asset Catalog, you can create service instances that are used by DTV (Digital Twin Visualization). The DTV finds the OData services through the DTV Service data assets that are created in the Data Asset Catalog so that you can manage the DTV Service data assets.

<br />

For more information about DTV (Digital Twin Visualization), see [Digital Twin Visualization Overview](/docs/app-development/en/dev/dtv/overview.html).

## Creating a DTV Service Data Asset

1. Log in to the **EnOS Management Console** and select **Data Asset Catalog** from the left navigation menu.

2. From the **New** drop-down menu on the left, select **DTV Service**.

3. On the **New DTV Service** page, complete the information for the following.
   - **ID**: Enter the ID of the DTV Service instance, which must be unique in the organization.
   - **Name**: Enter the name of the DTV Service instance.
   - **Host**: Enter the host of the OData service, using the standard URL format, for example, ``http://www.xxx.com/path``.
   - **OData Namespace**: Enter the OData namespace.
   - **Entity Declaration**: Enter the querying parameter for the OData metadata, which is used for filtering the entity metadata by entity name.
   - **$select Substitution**: Enter the parameter to use for substituting the $select parameter (the $select parameter does not support data fields like "site.XXX").
   - **Description**: Enter a short description for the DTV Service instance.

     .. image:: media/new_dtv_service_1.png

     <br />

4. Click **Add Parameter** to add and customize additional parameters.
   - **Name**: Enter the parameter name.
   - **Label**: Enter the parameter label.
   - **Type**: Select the parameter type. For enum type, select the **Enum Data Type**, and enter the **Enum Value**.

   <br />

5. Repeat step 4 to add more parameters.

   .. image:: media/new_dtv_service_2.png

   <br />

6. Click **Confirm** to save the DTV Service instance.


## Querying DTV Service Data Asset

The Data Asset Catalog enables you to query the metadata information of the created DTV Service data assets. You can search for DTV service data assets with the following steps.

1. Under the **Type** list on the left side of the **Data Asset Catalog** page, select **DTV service**.

2. In the search field, type keywords to search for DTV Service data assets.

   .. image:: media/dtv_search_result.png

<br />

.. note:: The search keywords are case sensitive and can match the ID, name, and description of the DTV Service data assets.

## Viewing, Editing, and Deleting DTV Service Data Assets

In the DTV Service search results, click the **View** icon to open and view the metadata of the DTV Service data asset.

### Basic Information

Under the **Basic Information** tab, you can view the basic information and parameters of the DTV Service data asset, such as:

- The ID, name, and description of the DTV Service data asset.
- The OData host and namespace.
- The OData metadata querying parameter and $select substitution parameter.
- The list of customized parameters.

.. image:: media/dtv_basic_info.png

<br />

To attach tags to the DTV Service data asset, click **Attach Tags** and select the pre-defined tag template in the pop-up window. Click the **Edit** or **Delete** icon to edit or delete the attached tags.

<br />

Click **Edit DTV Service** to update the DTV Service data asset, except for the ID.

<br />

Click **Delete DTV Service** to delete the DTV Service data asset. Note that the deleted DTV Service cannot be restored.


<!--end-->
