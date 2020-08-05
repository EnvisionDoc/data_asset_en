# Unit 3: Developing a Batch Processing Workflow

EnOS Batch Processing service enables you to process data through scheduling workflows, which consists of various types of tasks that can run data synchronization, Shell scripts, Python scripts, and external applications.

<br />

In this unit, develop a batch processing workflow with a Python task node to add measurement point data to TSDB.

## Developing a Workflow

Take the following steps to crate a workflow with Python task node:

1. Log in EnOS Management Console and select **Batch Processing > Data Development**.

2. Click the **+** icon to create a workflow. See the following example:

   .. image:: media/creating_workflow.png

3. From the Component panel, drag the PYTHON task node into the workflow panel.

4. In the **New Task Node** window, enter the name and description of the task, and click **Create**. See the following example:

   .. image:: media/creating_task_node.png

5. Double click the node that is created. In the **Command** field, enter the following Python script for writing measurement point data to TSDB:

   ```
   from Msg import MsgBuilder,MeasurepointBuilder

   import batchTSDBWriter

   def main():
       mp1 = MeasurepointBuilder.builder().add_measurepoint("mem_used", 92.8871579271854).add_measurepoint("cpu_used", 48.6415463007949).set_timestamp(1596420300000)

       #Provide the OU ID, model ID, and asset ID.
       #Use add_payload to upload the measurement point data.
       msg = MsgBuilder.builder("o15520323695671","Computer","vdVrfmo2").add_payload(mp1)

       #str(msg) is the message to be sent to Kafka.
       #The first parameter is of Boolean type. When False is specified, measurepoints will not be validated.
       #The second parameter is of Boolean type. When False is specified, assetId will not be validated.
       #The length of message must not exceed 3000 bytes.
       res = batchTSDBWriter.send_data(str(msg),True,True)

       if res == 0:
           return 0
       else:
           return -1
   ```

6. Click **Running Mode** at the right edge of the configuration panel and set the required resources for running the Python task. See the following example:

   .. image:: media/setting_running_mode.png

7. Click **Save** and **Back to Workflow Panel**. The workflow is created and configured.


## Running the Workflow

Take the following steps to run the created workflow:

1. On the **Workflow Panel**, click **Pre-run**, set the **Triggering Time**, and click **OK** to test running the workflow. See the following example:

   .. image:: media/running_workflow.png

2. Open the **Workflow Operation > Manual Instance** page to view the running status of the workflow instance.

   .. image:: media/viewing_workflow_instance.png

3. When the workflow instance runs successfully, click the instance name to view the running log.

   .. image:: media/viewing_workflow_log.png


## Next Unit

[Viewing Measurement Point Data](viewing_added_data)

<!--end-->
