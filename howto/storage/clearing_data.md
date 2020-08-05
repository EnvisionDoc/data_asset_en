# Deleting Data in TSDB

<br />

The EnOS Time Series Data Management supports the cleaning of the historical data (wrong data, informal data, or business data that is no longer needed) of assets that is stored in TSDB to release storage resource and reduce data storage costs. With the Data Deletion feature, you can delete the data of specific models, measurement points, and assets in the specified time range.

.. note:: Deleted data by data deletion jobs cannot be restored. You need to ensure that the specified data can be deleted to avoid data loss.

<br />

This section shows how to delete historical data stored in TSDB and view the data deletion records.

## Before You Start

Determine the model, measurement points, assets, and time range of the data to be deleted.

## Procedure

1. Log in to the **EnOS Management Console**, select **Time Series Data Management > Data Deletion**, and fill in the following under the **Data in TSDB** tab.

   - **Time**: Select the time range of the data to be deleted (by date and hours).

   - **Model**: Search for and select the model to which the data belongs to.

   - **Point**: Search for and select the measurement point to which the data belongs to.

   - **Asset**: Select one or multiple assets to which the data belongs to.

   <br />

2. Click the **Delete** button, and the system will start deleting data based on the specified conditions.

  .. image:: ../../media/data_cleanup.png

.. note:: Once submitted, the data deletion job cannot be cancelled, and the data cannot be restored once deleted.

## Results

The data deletion job will be displayed in the **Deletion Record** table.

1. Check the configuration details and status of the data deletion job.

   .. image:: ../../media/data_cleanup_status.png

   <br />

2. Click the **Detail** icon in the deletion record table to view the data deletion details.

   .. image:: ../../media/data_cleanup_details.png

   <br />

3. If the data deletion job failed, click the **Restart** icon in the deletion record table to restart the job. Note that deleted data cannot be restored.

## Next Step

You can check and verify whether the data has been deleted on the **Time Series Data Management > Data Insights** page.
