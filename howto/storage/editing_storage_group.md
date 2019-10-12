# Editing a TSDB Storage Policy Group
If you need to change the settings of a TSDB storage policy group, like adding models or removing selected models, you can edit the storage policy group.

1. On the **Time Series Data > Storage Policy** page, click the name of the storage policy group.

2. Click **Edit Group** to open the basic information page of the storage policy group.

3. Edit the group name if needed.

4. From the **Group Model** list, select new models or clear selected models to update the configuration. Then click **OK** to save the configuration.

.. note:: - If storage policy is already configured for measuring points of a model, you need to remove the storage policy configuration first. Otherwise, the selected model cannot be cleared.

     - A model can be associated to 1 storage policy group only.


## Deleting a TSDB Storage Policy Group
When stored data is not needed, you can delete TSDB storage policy groups to release resources and reduce costs.

1. On the **Time Series Data > Storage Policy** page, click the name of the storage policy group.
2. Click **More ...** and select **Delete Group**.

.. note:: A storage policy group can be deleted only if configured storage policies and associated models are removed. Deleting a storage policy group will remove all the stored historical data configured by the group.
