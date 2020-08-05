# Creating a Hive Table

<br />

This section shows how to create a Hive table using Zeppelin Notebook.


## About This Task
The data integrated from external data sources needs to be stored as Hive tables to be consumed by other EnOS data processing functions. You will need to create a Hive table with Zeppelin Notebook.

## Procedure

1. In the **EnOS Management Console**, click **Batch Processing > Data Sandbox** from the left navigation menu and open the Zeppelin Notebook.

2. Import or create a note.

   - If you already have a note created with table creation script included, click **Import note**.
   - If you want to create a note, click **Create new note**.

3. If you chose to create a note in step 2, enter a name for the note and select **hive** as the default interpreter. For example, if you entered `yourname/hive/tablename` as the note name, a hive table with the name `tablename` is created under the `yourname/hive` directory.

4. In the note, enter the commands to create the hive table. For example:

   ```
   %hive

   use db_name;

   CREATE TABLE IF NOT EXISTS employee(
      serial_id string,
      birthday string,
      first_name string,
      last_name string,
      gender string,
      onboard_date string)
      comment 'table for employee info'
      PARTITIONED BY (yyyymmdd string)
      STORED AS ORC;
   ```

   In the above example, replace `db_name` with the database name in the upper right corner of the Zeppelin Notebook page. For more information about the commands, see [Apache Hive documentation on table creation](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+DDL#LanguageManualDDL-CreateTable).


4. Click the **Run this paragraph** icon |Run_this_paragraph| . You will see your table created successfully as shown in the following screen capture:

   .. image:: media/create_hive.png


## Results
A hive table is created, and you can run a query to test the result.

```
%hive
select * from exployee limit 100
```

Run the query and you will get a result like this:

.. image:: media/test_query.png

## Next Step

If you are creating the Hive table to store data from external data source, you will then need to specify the table as a target and map columns from the data source to the target through Data Synchronization. For more information, see [Data Synchronization](/docs/data-asset/en/dev/howto/data_integration/index.html).

.. |Run_this_paragraph| image:: media/run.png

<!--end-->
