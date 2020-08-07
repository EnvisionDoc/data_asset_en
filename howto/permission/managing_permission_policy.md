# Managing Permission Policy

<br />

Through defining customized permission policies, you can grant the access permission of data assets to users of specified organizations.

## Prerequisites

- Data assets (such as HDFS files) already exist in your organization.
- Ensure that the users to be granted permission have the authorization to access the data assets of your organization.

## Adding Permission Policy

1. Log in to the **EnOS Management Console** and select **Data Asset Authorization** from the left navigation menu.

2. Click **Add Permission** and provide the following basic information.

   - **ID**: The ID is generated by the system.

   - **Policy Name**: Enter the name of the permission policy.

   - **Type**: Select the data asset type (only HDFS files are supported currently).

   - **Path**: Select the HDFS file type and file path (only HDFS FileSet is supported currently). You can select any of the registered HDFS fileset in the organization.

   - **Description**: Enter a short description for the permission policy.

     .. image:: ../../media/data_asset_permission_1.png

     <br />

3. In the **Permissions** section, click **Add** to enter the identity and permission for specific organizations.

   - **Authorized Identity**: Enter the IDs of organizations to be granted the data asset access (for example: *o15453595539601*). Organization IDs must be separated by commas.

   - **Permissions**: Select the operation permission(s) for the data asset from the drop-down.

     .. image:: ../../media/data_asset_permission_2.png

     <br />

4. Click **Confirm** to save the permission policy.

## Managing Permission Policy

All the added Data Asset Authorization policies are listed on the **Data Asset Authorization** page.

<br />

Based on your business needs, you can perform the following operations for the created policies.

- View the details of a permission policy: Click the **View** icon in the **Operations** column.
- Edit a permission policy: Click the **Edit** icon in the **Operations** column to update the basic information, and add or remove identities and permissions.
- Delete a permission policy: Click the **Delete** icon in the **Operations** column and click **Confirm**. Note that deleted policies cannot be restored.

<!--end-->