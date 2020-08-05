# Querying Measuring Point Metadata

<br />

With Data Asset Catalog, you can create a measurement point and query the metadata information of measurement points in the OU, including the basic information, TSBD storage policies, data archiving jobs, and related assets.

## Creating a Measurement Point

You can create a measurement point with the following steps.

1. Log in to the **EnOS Management Console** and select **Data Asset Catalog** from the left navigation menu.
2. From the **New** drop-down menu on the left, select **Point**.
3. On the **New Point** page, enter the ID, name, and description of the measurement point, and select the point type.
4. Click **Confirm** to create the measurement point.

.. image:: media/new_point.png

## Querying Measurement Points

The Data Asset Catalog enables you to query the metadata of all measurement points in the OU. You can search for measurement points with the following steps.

1. Under the **Type** list on the left side of the **Data Asset Catalog** page, select **Point**.

2. In the search field, type the keywords to search for the measurement points.

   .. image:: media/point_search_result.png

.. note:: The search keywords are case sensitive and can match the ID, name, and description of the measurement points.

## Viewing the Search Results

In the measurement point search results, click the **View** icon in the **Operations** column to open and view the metadata of the measurement point at the measurement point details page.

### Basic Information

Under the **Basic** tab, you can view the basic information of the measurement point, such as:

- The point ID, in the format of {model identifier}::{measurement point identifier}. If the measurement point is created through the Data Asset Catalog service, the Point ID will be the text entered for the **ID** field during creation.
- The point name and description.
- The point type.
- The person who created the point, and the time when the point was created and updated.
- The tags attached to the measurement point.

<br />

To attach tags to the measurement point, click **Attach Tags** and select the pre-defined tag template in the pop-up window. Click the **Edit** or **Delete** icon to edit or delete tags that are attached to the measurement point.

.. image:: media/attach_tags.png

### TSDB Storage

Click the **TSDB Storage** tab to view the basic information of the TSDB storage policies configured for the measurement point as per the below.

- Storage policy group
- Data storage type
- Storage time
- Storage scope

.. image:: media/point_storage_policy.png

### Archiving Job

Click the **Archive Job** tab to view the information of the data archiving jobs configured for the measurement point as per the below.

- Name and description of the archiving job
- Storage type and resource
- Storage path and file name
- Data archiving period

<!--

.. image:: media/point_archiving_job.png

-->

### Related Asset Information

Click the **Related Asset** tab to view all the asset instances associated with the model to which the measurement point belongs. In the **Operations** column, click the links to view more information for the following.

<br />

- **Detail**: View the metadata information of the asset.

- **Data Quality**: View the data quality details of the asset and measurement point.

- **Data Insights**: View the measurement point data of the asset stored in TSDB.

<!--

.. image:: media/point_related_assets.png

-->

<!--end-->
