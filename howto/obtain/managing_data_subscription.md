# Developing Data Subscription Jobs
EnOS System provides data subscription service to improve the API calling efficiency of applications with active push of subscribed data, which supports subscription to real-time asset data, asset alert data, and asset meta data. Benefiting from the data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, applications can call APIs only when there are pushed data, thus improving API calling efficiency and reducing costs.



## Data Subscription Workflow
.. image:: ../../media/data_subscription_process.png

## Creating a Subscription Job
Take the following steps to create a data subscription job:

1. Log in EnOS Console and select the **Data Subscription** module. On the **Data Subscription** page, click the **New Subscription** button to open the subscription configuration page.

   .. note:: An organization can have at most 5 data subscription jobs.

2. Select the data subscription type, which determines the data source to be subscribed to. The subscription configuration for data sources is different. EnOS data subscription service supports the following data sources:

   - **Real-time data**: Real-time telemetry of asset measuring points uploaded to the cloud with time stamp.
   - **Alert data**: Alert data are generated according to specific alert rules defined for real-time data.

3. In the **ID** field, enter an ID for the subscription job or click **Generate** to use the system-generated ID. The subscription ID is a mandatory parameter for consuming subscribed data.

4. From the **SA** drop down list, select the SA (service account) that is used for client and data authentication. Each subscription topic must has an associated SA. The system will detect the validity of the service account dynamically. When a service account is deleted, the data subscription configuration will be automatically disabled.

   .. note:: The SA account associated with the data subscription job must be authorized to access the asset data. Otherwise, the data subscription job will fail because of authentication failure. For more information about authorizing the SA account, see [Managing Service Accounts](/docs/enos/en/2.0.9/iam/howto/service_account/managing_service_account.html). 

5. In the **Description** field, enter a short description for the subscription job.

6. For the **Clients** section, choose the clients whose data are to be subscribed to based on the data access permission of the selected SA (associated with purchased application).

   .. note:: When a client revokes the data access authorization of a service account, the related subscription to the client's data will be stopped automatically.

7. Complete the data filtering configurations for real-time data subscription and alert data subscription separately:

   - For **Real-time data** subscription: Filtering data by model and measuring points (subscribing to data of specific measuring points) and optionally by device tags (subscribing to data of specific devices).
   - For **Alert data** subscription: Filtering data by models (subscribing to alert data of specific model) and optionally by device tags or asset tree tags (subscribing to data of specific devices or asset trees).

8. Click **Save** to save the data subscription configuration.

.. note:: When a subscribed data source (model or measuring point) is deleted, the system will keep the data subscription configuration, but an error message will be displayed, reporting that the configured data source is an unknown object.



## Enabling the Subscription Job

After the subscription job is configured, find the saved topic on the **Data Subscription** page, and click the **Enable** icon to run the subscription job. The data producer will start writing data to the topic.



## Deleting the Subscription Job

You can choose to delete a subscription job on the **Data Subscription** page. Note that jobs in running status cannot be deleted and that deleted jobs cannot be restored.
