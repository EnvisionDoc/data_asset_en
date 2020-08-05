# Batch Processing Overview

<br />

Data developers can use the Batch Processing service to process data through scheduling workflows.

## Key Concepts

### Workflow

A workflow is an automatic data processing flow that consists of  _tasks_, _references_, and _relations_. A workflow is a directed acyclic graph (DAG), and it cannot be a circular workflow.
A workflow can be scheduled to run only once or periodically.

### Task

A task is the fundamental element of the workflow where it defines how to process the data. By running a task, the resource associated with the task is run. The Batch Processing service provides the following types of tasks:

- Data synchronization task: A data synchronization task will synchronize data from an external data source to the EnOS Hive library. For more information, see [Data Synchronization](../data_integration/index).

- SHELL task: A task that runs Shell script.

- External APP: Running external applications as task node.

- PYTHON task: A task that runs Python script.

### Reference

A reference is a task or workflow that is the prerequisite of its subsequent tasks. A reference must be the root node of a workflow. A workflow can have more than one reference. Regardless of the scheduling settings of a task, the task is not run until its reference is run.

### Relation

An upstream task connects to a downstream task through relations. The relation is uni-directional.

### Resource

A resource is the script that is run by SHELL and PYTHON tasks. The supported resource formats are: `sh`, `jar`, `sql`, `hql`, `xml`, `zip`, `tar`, `tar.gz`, and `py`.

## Stages of Data Development

The data development process has the following stages.

### Configuration Stage  

During configuration, you can create a workflow that has running tasks, and pre-run the workflow to verify whether the workflow runs as designed.

### Running Stage

At the running stage, the workflow will run according to the scheduling parameters.

### Monitoring Stage

At the monitoring stage, you can rerun a single task node or rerun a node and its subsequent nodes to pinpoint issues with the workflow.

<br />

The following figure shows an example workflow with a reference.

.. image:: media/workflow_reference.png
      :width: 400px

<br />

1. Task 1 and Task 2 will not run until the reference is run.

2. If the workflow is a periodic workflow, all tasks are run at each cycle as defined by the scheduling parameters.

3. `True` and `False` is only applicable at the monitoring stage when you rerun a task.

   - When `True`, the subsequent task is run.
   - When `False`, the subsequent task is not run.


## Major Functionalities

### Workflow Development

According to your business requirements, you can design a workflow that has multiple tasks, and each task performs certain actions on your data.

### Job Resource

You can register your scripts as resources and manage the version of the resources. The resources can then be referenced by tasks in a workflow.

## Typical User Scenarios for Data Development

### Running a Built-in Script

EnOS provides built-in scripts for the most frequently used data processing activities, such as synchronizing the master data from HDFS to an external S3 database, or converting columns to rows. For a complete list of built-in scripts that EnOS provides, see [Common Library](common_library).

<br />

The major procedure of running a built-in script is as per the below.

1. In **Batch Processing > Data Development**, browse the Common Library tree and locate the script that you want to run.

2. Double-click the version of the script and review the details about the script.

   <!-- .. image:: ../../media/scenario_built-in.png
      :alt: Figure: Built-in script

    <br /> -->


3. Click **Use the Program**.

4. Provide the workflow settings in the pop-out window.

   .. image:: ../../media/built-in_workflow.png
      :alt: Figure: Workflow with bulit-in script

   <br />


5. Provide the scheduling settings. For more information, see [Creating a One-time Workflow](data_dev/creating_workflow_onetime) or [Creating a Periodic Workflow](data_dev/creating_workflow_periodic).


### Running an External Script

The major procedure of running an external script is as per the below.

1. Upload your script as a resource on EnOS. For more information, see [Creating a Resource](job_resource/creating_resource).

2. Create a workflow with a SHELL task that references the resource. For more information, see [Creating a One-time Workflow](data_dev/creating_workflow_onetime) or [Creating a Periodic Workflow](data_dev/creating_workflow_periodic) according to your needs.

## Resource Preparation

<br />

**Batch Processing - Container**

Before configuring batch data processing tasks, ensure that your OU has requested for the **Batch Processing - Container** resource via the **EnOS Management Console > Resource Management** page. The resource specification determines the data processing capability of the tasks. For more information about requesting for the **Batch Processing - Container** resource, see [Resource Specifications](/docs/enos/en/dev/resourcemanagement/reference/index.html).

<br />

When you do not need to process batch data with the Batch Processing service, you can delete and release the requested resources through the **Resource Management** page to save costs.
