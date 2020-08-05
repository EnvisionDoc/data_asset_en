# Supported System Variables

<br />

You can not only use variables in path and parameter settings, but also  directly in your SHELL script.

<br />

For example, in creating a data synchronization job for synchronizing data from EnOS Hive to a target database, when setting the partition value, you can select **Placeholder** as the method of specifying the partition, and enter the name of the system variable to be used. The system will load partition information automatically according to the specified variable.

## Business-related Variables

Before you start to use the service-related variables, note the following key concepts.

### Triggering Time

The time when a workflow is triggered. It can be the time when you manually trigger the workflow, or when the workflow is automatically triggered according to scheduling settings.

### Business Date

The date when the workflow starts to process the data. The date is calculated by deducting one day from the triggering time (because the workflow processes the data of the previous day by default). 

<br />

For example, if the triggering time is `2017-05-27 13:50:00`, and the scheduled cycle is one day, the business date will be `2017-05-26`, which means that the data on `2017-05-26` will be processed at the triggering time `2017-05-27 13:50:00`. Therefore, if you want to process data for 2018-03-01, you need to set the triggering time to 2018-03-02.

<br />

The following table explains the system variables by using `2017-05-27 13:50:00` as the example triggering time.

.. list-table::
   :widths: 15 40 20 15 10
   :header-rows: 1

   * - Variable
     - Description
     - Format
     - Business Date
     - Variable Value
   * - ${last_week8}
     - + Based on triggering time: indicates last week.
       + Based on business date: indicates business date minus 6 days.
     - YYYYMMDD
     - 2017-05-26
     - 20170520
   * - ${last_week10}
     - + Based on triggering time: indicates last week.
       + Based on business date: indicates business date minus 6 days.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-20
   * - ${cal_dt}
     - + Based on triggering time: indicates yesterday.
       + Based on business date: indicates today.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-26
   * - ${cal_dt8}
     - + Based on triggering time: indicates yesterday.
       + Based on business date: indicates today.
     - YYYYMMDD
     - 2017-05-26
     - 20170526
   * - ${cal_dt-n}
     - + Based on triggering time: indicates n+1 days before today.
       + Based on business date: indicates n days before today.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-25
   * - ${cal_dt8-n}
     - + Based on triggering time: indicates n+1 days before today.
       + Based on business date: indicates n days before today.
     - YYYYMMDD
     - 2017-05-26
     - 20170525
   * - ${ncal_dt}
     - + Based on triggering time: indicates today。
       + Based on business date: indicates today+1.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-27
   * - ${ncal_dt8}
     - + Based on triggering time: indicates today.
       + Based on business date: indicates today+1.
     - YYYYMMDD
     - 2017-05-26
     - 20170527
   * - ${end_day_this_month8}
     - Based on business date: indicates the last day of this month.
     - YYYYMMDD
     - 2017-05-26
     - 20170531
   * - ${end_day_this_month10}
     - Based on business date: indicates the last day of this month.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-31
   * - ${first_day_this_month8}
     - Based on business date: indicates the first day of this month.
     - YYYYMMDD
     - 2017-05-26
     - 20170501
   * - ${first_day_this_month10}
     - Based on business date: indicates the first day of this month.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-01
   * - ${first_day_last_month8}
     - Based on business date: indicates the first day of last month.
     - YYYYMMDD
     - 2017-05-26
     - 20170401
   * - ${first_day_last_month10}
     - Based on business date: indicates the first day of last month.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-04-01
   * - ${last_day_last_month8}
     - Based on business date: indicates the last day of last month.
     - YYYYMMDD
     - 2017-05-26
     - 20170430
   * - ${last_day_last_month10}
     - Based on business date: indicates the last day of last month.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-04-30
   * - ${monday_next_week8}
     - Based on business date: indicates next Monday.
     - YYYYMMDD
     - 2017-05-26
     - 20170529
   * - ${monday_next_week10}
     - Based on business date: indicates next Monday.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-05-29
   * - ${30days_cal_dt}
     - Based on business date: indicates 30 days ago.
     - YYYY-MM-DD
     - 2017-05-26
     - 2017-04-26
   * - ${hcal_dt8}
     - Based on business date and time: indicates 1 hour ago. Variable value is the current date.
     - YYYYMMDD
     - 2017-05-26 00:30:00
     - 20170525
   * - ${cal_hr}
     - Based on business date and time: indicates 1 hour ago. Variable value is the current hour-level number.
     - HH
     - 2017-05-26 00:30:00
     - 23

## Time Related Vriables

The following table explains the time-related variables by using `2017-05-27 13:50:00` as the example triggering time.

.. list-table::
   :widths: 25 35 40
   :header-rows: 1

   * - Variable
     - Description
     - Value
   * - ${this_hour}
     - The hour when the workflow is triggered.
     - 2017-05-27 13:00:00
   * - ${unix_timestamp}
     - The Unix time corresponding to the triggering time.
     - 1495864241


## Non-time related variables

.. list-table::
   :widths: 25 40 35
   :header-rows: 1

   * - Variable
     - Description
     - Example
   * - ${task_id}
     - The task ID of the current instance.
     - 2017-05-27 13:00:00
   * - ${instance_id}
     - The current instance ID.
     - 1495864241
   * - ${env.APP_CUSTOMER}
     - The group account of the user who generated the instance.
     - CLP
   * - ${env.APP_ID}
     - The App ID that the instance belongs to.
     - a22b94f9-3b9d-40f6-9bd8-4d66b304d930

<!--end-->
