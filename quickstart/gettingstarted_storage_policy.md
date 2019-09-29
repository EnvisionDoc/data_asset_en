# Getting Started: Configuring Data Storage

This guide introduces how to quickly configure TSDB data storage and retrieve the stored data with EnOS Open APIs.

## Prerequisites

- Access permission to the Storage Policy module of the Time Series Data service.
- Device connection is completed, and the devices are uploading data to EnOS.

## About This Task

**Goal**

The goal of this guide is to store the AI type raw data of the *test_raw* measuring point in TSDB as minute-level data, and then invoke an API to get the maximum value of the *test_raw* point every 5 minutes in a specific time range.

**Data Preparation**

Model configuration: Detailed information about the (*test_Model*) used for this guide is as follows:

.. list-table::

   * - Feature Type
     - Name
     - Identifier
     - Point Type
     - Data Type
   * - Measuring Point
     - test_raw
     - test_raw
     - AI
     - DOUBLE

For instructions on creating and configuring models, see [Creating a Model](/docs/device-connection/en/2.0.9/howto/model/creating_model.html).

## Procedure

The steps for configuring data storage policies and retrieving stored data are as follows:

- Create a storage group in TSDB Storage
- Configure and save a TSDB storage policy
- Retrieve and aggregate data with Open API

### Step 1. Create a Storage Policy Group

Log in EnOS Console and select **Time Series Data > Storage Policy**. Click **New Group** to create a storage policy group. Enter the group name, select a group model (select *test_Model* for this guide), and click **OK** to save the storage group configuration.

### Step 2. Configure Storage Policy

After the storage group is created, you can see all the TSDB storage policy options listed under the storage group tab. Select the **AI Normalized Data** policy for this guide by clicking the Edit icon in the upper right corner of the tile. On the **Edit Storage Policy** page, complete the following configuration:

- **Storage Time**: Select the data storage time (for example, 1 month).
- **Select Points**: Select models and corresponding measuring points. Data of the selected measuring points will be stored according the storage policy configuration. Select the *test_raw* point of the *test_Model* model for this guide.

Click **OK** to save the storage policy configuration. The system will store the data of the *test_raw* measuring point according to the configuration. For this guide, the second-level suffix of the data time stamp will be removed when the AI data is stored in TSDB. Therefore, only the last-coming data record of a minute will be stored.

### Step 3. Retrieve stored data with API

Use the *Get Asset AI Data with Aggregation Logic* API to retrieve the stored normalized data of the measuring point. For sample code of calling the TSDB Data Service API, go to **EnOS Console > EnOS API**.
