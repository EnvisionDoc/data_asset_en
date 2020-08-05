# Creating a TSDB Storage Policy Group

<br />

TSDB storage policy groups support separate storage policy configurations of different projects or domains for easy management. Each storage policy group has the same set of storage types. Before configuring the data storage policy for your asset data, you need to create a storage policy group.

<br />

Create a TSDB storage policy group with the following steps.

1. Log in the **EnOS Management Console** and select **Time Series Data Management > Storage Policy**.

2. Click the **+** icon in the upper right corner of the page and select **Create Group**.

3. Complete the configuration of the storage policy group:

   - **Group Name**: Enter a name for the storage policy group. Chinese characters, English letters, underscores, and hyphens are supported.

   - **Group Model**: Search and select the models to be associated with the storage policy group.

   .. note:: Before configuring the storage policy for measurement points, you must associate the asset model with a storage policy group, so that the storage policy can be configured for the measurement points of the model. A model can be associated with 1 storage policy group only.

4. Click **OK** to finish creating the storage policy group.

   .. image:: ../../media/storage_policy_group.png

<!--end-->
