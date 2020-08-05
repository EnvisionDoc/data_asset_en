# Querying Hive Table Metadata

<br />

With Data Asset Catalog, you can query the metadata information of Hive tables in the OU, including the basic information, schema, partition list, and service list.

## Querying Hive Tables

The Data Asset Catalog enables you to query the metadata information of all the Hive tables created in the OU. You can search for an Hive table with the following steps.

1. Log in to the **EnOS Management Console** and select **Data Asset Catalog** from the left navigation menu.
2. Under the **Type** list on the left, select **Hive Table**.
3. In the search field, type the keywords to search for Hive tables.

.. image:: media/table_search_result.png

.. note:: The search keywords are case sensitive and can match the ID, name, and description of the Hive tables.

## Viewing the Search Results

In the Hive table search result list, click the **View** icon in the **Operations** column to open and view the metadata of the Hive table at the Hive table details page.

### Basic Information

Under the **Basic** tab, you can view the basic information of the Hive table, such as:

- The name and description of the Hive table.
- Whether the Hive table is an external table.
- The storage URL of the Hive table.
- The person who created the Hive table, and the time when the table was created and updated.
- The tags attached to the Hive table.

<br />

To attach tags to the Hive table, click **Attach Tags** and select the pre-defined tag template in the pop-up window. Click the **Edit** or **Delete** icon to edit or delete tags that are attached to the Hive table.

.. image:: media/table_basic_info.png

### Schema

Click the **Schema** tab to view detailed information of the Hive table schema as per the below.

- Column name
- Data type
- Whether it is a partition
- Description

.. image:: media/table_schema.png

### Partition List

Click the **Partitions** tab to view the list of Hive table partitions which shows the details below.

- Partition Name
- Data Type
- Time when the partition was created

.. image:: media/table_partition.png

### Service List

Click the **Services** tab to view the list of Hive table services which shows the details below.

- Service name and description
- Service URL

<!--end-->
