# Creating a TSDB Storage Policy Group
TSDB storage policy groups support separate storage policy configuration of different projects or domains for easy management. Each storage policy group has the same set of storage types. Before configuring data storage policy for your asset data, you need to create a storage policy group.

Take the following steps to create a TSDB storage policy group.

1. Log in EnOS Console and select **Time Series Data > Storage Policy**.

2. Click **Create Group** or the **+** icon to create a storage policy group. Then, complete the configuration of the storage policy group.

   - **Group Name**: Enter a name for the storage policy group. Chinese characters, English letters, underscores, and hyphens are supported.
   - **Group Model**: Search and select the models to be associated with the storage policy group.

   .. note:: Before configuring storage policy for measuring points, you must associate the asset model with a storage policy group, so that storage policy can be configured for measuring points of the model. A model can be associated with 1 storage policy group only.

3. Click **OK** to create the storage policy group.

See the following screen capture for creating a storage policy group.

.. image:: ../../media/storage_policy_group.png

<!--end-->
