# Creating a Periodic Workflow from Scratch

<br />

This section shows how to create a periodic workflow that is run automatically based on the scheduling parameters.

## Before You Start

Ensure that you have created the codes and scripts needed for running the data as resources. For more information, see [Creating a Resource](../job_resource/creating_resource).

.. note:: A periodic workflow cannot be changed to one-time workflow after creation.

## Step 1: Create a Workflow

1. In the **EnOS Management Console**, click **Batch Processing > Data Development** from the left navigation menu and click **+** to create a workflow.

2. In the **New Workflow** window, provide the following settings and click **OK**.

   - **Mode**: Choose whether to create a workflow from scratch or by importing a configuration file.
   - **Name**: Enter the name of workflow.
   - **Type**: Select **Periodic scheduling**.
   - **Description**: Provide a description for the workflow.
   - **Select Dir**: Select the directory to store the workflow.

## Step 2: (Optional) Add References

If the workflow is dependent on another workflow or task, reference it as the root node.

- To reference a workflow, drag the **Flow Ref** under **Reference** into the workflow panel, select the workflow, and click **Create**.
- To reference a task, drag the **Task Ref** under **Reference** into the workflow panel, select the task, and click **Create**.

.. note:: - To reference a task node, you must set the task node to allow reference in the **Node Scheduling Config** of the task node.
      - A task node that allows reference must be a periodic task.
      - A workflow or task node is referenced by selecting its instance ID, which can be found on the **Workflow Operation** page (clicking the task name to view the instance ID).

<br />

Repeat if the workflow depends on multiple references.

## Step 3: Add Task Nodes

### Add a Data Synchronization Task Node

1. From the **Component** panel, drag the **Data Sync** task node into the workflow panel.

2. In the **New Task Node** window, enter the name and description of the task. Note that a task is unique within the same workflow.

3. Select the type of the data to be synchronized: **Structured data** or **File stream**.

4. Click **Create**.

5. Double click the node that you just created and complete the configuration of the data synchronization task. For the detailed steps, see [Data Synchronization Overview](../../data_integration/di_overview).

6. Click **Node Scheduling Config** at the right edge of the configuration panel and provide the following scheduling settings.
   - **Specific Time**: Specify the time to run the task with CronTab syntax. For example, the value `59 59 23 * * ? *` represents running the task at 23:59:59 every day. For more information about CronTab, see the [Cron Expression Explainer](http://www.freeformatter.com/cron-expression-generator-quartz.html).
   - **Timeout**: The timeout value.
   - **Retry Times**: The number of reconnection attempts to try after timeout.
   - **Retry Interval**: The interval between each reconnection attempt.
   - **Allow Reference**: Select whether the task can be referenced.

7. If parameters are used in the task, click **Parameter Settings** at the right edge to specify the parameter values. You can use constants, system variables, or custom variables for a parameter. For more information, see [Setting Parameters](setting_parameters).

8. Click the **Running Mode** at the right edge of the configuration panel and set the container resources that are required by running the task.

9. Click **Save** and click **Back to Workflow Panel**.


### Add a SHELL Task Node

1. From the **Component** panel, drag the **SHELL** task node into the workflow panel.

2. In the **New Task Node** window, enter the name and description of the task. Note that task is unique within the same workflow.

3. Click **Create**.

4. Double click the node that you just created.

5. Enter the command to run, select the resource, and the resource version.

6. Click **Node Scheduling Config** at the right edge of the configuration panel and complete the scheduling attribute configuration.

7. If parameters are used in the task, click **Parameter Settings** at the right edge to specify the parameter values. You can use constants, system variables, or custom variables for a parameter. For more information, see [Setting Parameters](setting_parameters).

8. Click **Save** and click **Back to Workflow Panel**.


### Add an External APP Task Node

1. From the **Component** panel, drag the **External APP** task node into the workflow panel.

2. In the **New Task Node** window, enter the name and description of the task. Note that task is unique within the same workflow.

3. Click **Create**.

4. Double click the node that you just created.

5. Enter the domain name of the application and the command to run (if extra parameters are needed in the command, configure the parameter in the **Parameter Config** at the right edge of the configuration panel).

6. Click **Node Scheduling Config** at the right edge of the configuration panel and complete the scheduling attribute configuration.

7. If parameters are used in the task, click **Parameter Settings** at the right edge to specify the parameter values. You can use constants, system variables, or custom variables for a parameter. For more information, see [Setting Parameters](setting_parameters).

8. Click **Save** and click **Back to Workflow Panel**.


### Add a PYTHON Task Node

1. From the **Component** panel, drag the **PYTHON** task node into the workflow panel.

2. In the **New Task Node** window, enter the name and description of the task. Note that task is unique within the same workflow.

3. Click **Create**.

4. Double click the node that you just created.

5. In the **Command** field, enter the command to run, and select the corresponding resource and the resource version (The Python script to be run must be already uploaded through the **Job Resource** page. For more information about how to access data sources by Python, see [Accessing Data Sources by Python](accessing_by_python)).

6. Click **Node Scheduling Config** at the right edge of the configuration panel and complete the scheduling attribute configuration.

7. If parameters are used in the task, click **Parameter Settings** at the right edge to specify the parameter values. You can use constants, system variables, or custom variables for a parameter. For more information, see [Setting Parameters](setting_parameters).

8. Click the **Running Mode** at the right edge of the configuration panel and set the running mode of the Python task.

   - Single Task: Set the container resources that are required by running the task.
   - Multiple Tasks: Set the container resources that are required by running the task, the maximum concurrency, and specify the source of the distribution key (from external files or custom key).

9. Click **Save** and click **Back to Workflow Panel**.


## Step 4: Add Relations

1. From the **Component** panel, click **Relation**.
2. Move the cursor to the upstream task node, click and drag the cursor, and an arrowhead will appear.
3. Drag the arrowhead to the downstream task node.
4. Repeat steps 2 and 3 until you finish connecting all the nodes according to your design.

.. note:: References must always be the root node.

## Step 5: Configure Scheduling Settings

1. Click **Scheduling Config** from the right edge of the configuration panel.

2. Provide the basic settings for the below.

   - **Owner**: Select the workflow owner from the list of users in the organization who have access to the Data Synchronization service. The workflow creator is added by default.
      - As the creator, you cannot delete yourself.
      - You can add other owners in the same organization.
      - The same owner is not allowed to create another workflow with the same name.
   - **Description**: (Optional) Provide a description.
   - **Alert Mode**: Select how to alert the workflow owner. Email is always selected by default, and cannot be unselected.
      - E-mail: an alert e-mail is sent to the owner when an instance meets the alert conditions. When the task fails, a copy of the alert is also sent to the affected downstream task owner, if an owner is assigned.
      - SMS: To use this feature, the user's phone number must be verified during user registration. Note that the SMS alert is sent to only the owner when an instance meets the alert conditions.

3. Provide the scheduling settings.

   - **Effective Date**: Specify when the task will start to take effect.
   - **Scheduling Cycle**: Specify how frequent to run the task. For example, you can specify to run the task on a daily basis. You can also select to use the CronTab expression.
   - **Specific Time**: Based the cycle you select, specify the exact time in a cycle to run the task. For example, you can specify to run the task at 9:00 am everyday. If you chose the CronTab syntax, enter the 7-character CronTab expression. For example, the value `59 59 23 * * ? *` indicates that the task is to run at 23:59:59 every day. For more information about CronTab, see the [Cron Expression Explainer](http://www.freeformatter.com/cron-expression-generator-quartz.html).

## Step 6: Specify Parameters

If parameters are used when you configure the data source and target, specify the parameter values by clicking **Parameter Config** at the right edge of the configuration panel. For more information, see [Setting Parameters](setting_parameters).

## Next Step

Click **Pre-run** to test the result of the workflow.

<br />

After a workflow starts to run, an instance will be generated. You can then trace the details about the instance through **Workflow Operation**. For more information, see [Monitoring Periodic Workflow Instances](../task_monitor/monitoring_workflow_periodic).

<br />

After the data is synchronized from the data source, you can schedule other processing tasks based on the data. For more information, see [Batch Processing Overview](../dataide_overview).
