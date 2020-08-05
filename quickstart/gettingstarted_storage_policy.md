# Getting Started: Configuring Data Storage

<br />

This section shows how to quickly configure TSDB data storage and retrieve the stored data with EnOS Open APIs.

## Prerequisites

- You have access permission to the Storage Policy module of the Time Series Data service.
- Device connection is completed, and the devices are uploading data to EnOS.
- Your OU has requested for the TSDB resource through Resource Management.

## Procedure

The steps for configuring data storage policies and retrieving stored data are as follows:

- Create a storage policy group
- Configure and save TSDB storage policy
- Retrieve and aggregate data with Open API


## Goal and Preparation

<br />

**Goal**

The goal of this guide is to store the AI type raw data of the *test_raw* measurement point in TSDB as minute-level data, and then invoke an API to get the maximum value of the *test_raw* point every 5 minutes within a specific time range.

<br />

**Data Preparation**

Model configuration: The detailed information about the (*test_Model*) used for this guide is as follows.

.. list-table::
   :header-rows: 1

   * - Feature Type
     - Name
     - Identifier
     - Point Type
     - Data Type
   * - Measurement Point
     - test_raw
     - test_raw
     - AI
     - double

For instructions on creating and configuring models, see [Creating a Model](/docs/device-connection/en/dev/howto/model/creating_model.html).


### Step 1. Create a Storage Policy Group

If no storage policy group is created, create a storage policy group and associate the *test_Model* with the storage policy group.

1. Log in to the **EnOS Management Console** and select **Time Series Data Management > Storage Policy**.

2. Click the **+** icon in the upper right corner of the page, and select **Create Group** (creating a storage policy group for this guide).

3. Enter the group name, search and select the models (*test_Model* for this guide) to be associated with the storage policy group.

4. Click **OK** to save the storage policy group configuration.

### Step 2. Configure Storage Policy

After the storage group is created, you can see all the TSDB storage policy options listed under the storage group tab. Select the **AI Normalized Data** policy for this guide by clicking the Edit icon in the upper right corner of the tile. On the **Edit Storage Policy** page, complete the following configuration.

- **Storage Time**: Select the data storage time (for example, 1 month).

- **Select Points**: Select the models and corresponding measurement points. Data of the selected measurement points will be stored according the storage policy configuration. Select the *test_raw* point of the *test_Model* model for this guide.

<br />

Click **OK** to save the storage policy configuration. The system will store the data of the *test_raw* measurement point according to the configuration. For this guide, the second-level suffix of the data timestamp will be removed when the AI data is stored in TSDB. Therefore, only the last-coming data record of one minute will be stored.

### Step 3. Retrieve stored data with API

Use the *Get Asset AI Data with Aggregation Logic* API to retrieve the stored normalized data of the measurement point. For the sample code of calling the TSDB Data Service API, go to **EnOS Management Console > EnOS API**.
