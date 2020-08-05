# Querying Asset Metadata

<br />

With Data Asset Catalog, you can query the metadata information of an asset, including the basic information of the asset, tags attached to the asset, and a complete list of all the measurement points for the asset.

## Querying Assets

The Data Asset Catalog enables you to query the metadata information of all assets in the OU. You can search for an asset with the following steps.

1. Log in to the **EnOS Management Console** and select **Data Asset Catalog** from the left navigation menu.
2. Under the **Type** list on the left, select **Asset**.
3. In the search field, type the keywords to search for assets.


.. image:: media/asset_search_result.png


.. note:: The search keywords are case sensitive and can match the ID, name, and description of the assets.

## Viewing the Search Results

In the asset search result list, click the **View** icon in the **Operations** column to open and view the metadata of the asset at the asset details page.

### Basic Information

Under the **Basic** tab, you can view the basic information of the asset, such as:

- The asset ID.
- The name and description.
- The timezone of the location where the asset is located.
- The person who created the asset, and the time when the asset was created and updated.
- The tags attached to the asset.

<br />

To attach tags to the asset, click **Attach Tags** and select the pre-defined tag template in the pop-up window. Click the **Edit** or **Delete** icon to edit or delete tags that are attached to the asset.

.. image:: media/attach_tags.png

### Measurement Point List

Click the **Points** tab to view all the measurement points of the asset, including:

- The measurement point ID. Click an ID to query the metadata information of the measurement point.
- The name and description.
- The measurement point type.

.. image:: media/asset_point_list.png

<!--end-->
