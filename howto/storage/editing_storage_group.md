# Editing a TSDB Storage Policy Group

<br />

If you need to change the settings of a TSDB storage policy group, such as adding models or removing selected models, you can edit the storage policy group to do so.

1. On the **Time Series Data Management > Storage Policy** page, click the name of the storage policy group.

2. Click **Edit Group** to open the basic information page of the storage policy group.

3. Edit the group name if needed.

4. From the **Group Model** list, select new models or clear selected models to update the configuration. Then click **OK** to save the configuration.

.. note:: - If the storage policy is already configured for the measurement points of a model, you need to remove the storage policy configuration first. Otherwise, the selected model cannot be cleared.

     - A model can be associated to only 1 storage policy group.


## Deleting a TSDB Storage Policy Group

When the stored data is not needed, you can delete TSDB storage policy groups to release resources and reduce costs.

1. On the **Time Series Data Management > Storage Policy** page, click the name of the storage policy group.

2. Click **... More** and select **Delete Group**.

.. note:: A storage policy group can be deleted only if its configured storage policies and associated models are removed. Deleting a storage policy group will remove all the stored historical data configured by the group.


## Releasing TSDB Resource

When your OU does not need to store data in TSDB, you can delete the requested TSDB resources through the **EnOS Management Console > Resource Management** page. Before deleting the TSDB resources, you must delete all the storage policy groups first.

<!--end-->
