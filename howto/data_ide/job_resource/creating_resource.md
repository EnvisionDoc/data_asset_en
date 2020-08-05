# Creating a Resource

<br />

The section shows how to create a resource and add new versions of the resource.

## Procedure

1. In the **EnOS Management Console**, click **Batch Processing > Job Resource** from the left navigation menu and click **Create Resource**.

2. In the **Create Resource** window, provide the basic settings for the resource.

   - **Name**: Enter a name for the resource.
   - **Description**: Provide a description for the resource.
   - **Select Directory**: Select the directy to save the resource.

   <br />

3. Click **OK**.

4. In the **Overview** page, click the **New Version** button to add a resource version.

   - **Upload**: From your local file system, browse to and select the script file.
   - **Version**: Specify the version of the resource using the format `v<version_number>.<release_number>.<modifier_number>`. For example, v1.0.0.      
   - **Description**: Provide a description for the version.

   <br />

5. Click **OK**.  

6. Repeat steps 4 to 5 to add more versions for the resource.

## Next Step

You can then invoke the scripts packaged in the resource through a SHELL task in a workflow.

## References

- [Creating a One-time Workflow from Scratch](../data_dev/creating_workflow_onetime)
- [Creating a Periodic Workflow from Scratch](../data_dev/creating_workflow_periodic)
