# Creating a Workflow by Importing an Existing Configuration

<br />

If you have an existing workflow configuration that you want to reuse for the new workflow, you can import the configuration file.

## Before You Start

Ensure that you have a workflow configuration file stored locally. For information about how to export an existing workflow as a configuration file, see [Exporting a Workflow](operating_workflow#exporting-a-workflow).

## Procedure

1. In the **EnOS Management Console**, click **Batch Processing > Data Development** from the left navigation menu and click **+** to create a workflow.

2. In the **New Workflow** window, provide the following settings and click **OK**.

   - **Mode**: Select **Import task config**.   
   - **Name**: Enter the name of workflow.
   - **Upload File**: In your local file system, browse to and select the configuration file.
   - **Description**: Provide a description for the workflow.
   - **Select Directory**: Select the directy to save the workflow.

3. Click **OK**.

4. Edit the settings that are loaded from the configuration file.

   - If the imported configure file defines a periodic workflow, see [Creating a Periodic Workflow from Scratch](creating_workflow_periodic).
   - If the imported configure file defines a one-time workflow, see [Creating a Manual Workflow from Scratch](creating_workflow_onetime).

## Next Step

Pre-run the workflow to test the result of your configuration.
