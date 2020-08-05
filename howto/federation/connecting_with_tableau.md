# Connecting with Tableau through JDBC

<br />

The Data Federation service enables the reading of data from data sources through the JDBC interface in Tableau.

<br />

This section shows how to connect data sources in Tableau through the JDBC interface.

## Prerequisites

- You have installed Tableau Desktop edition (2020.1 or newer version is recommended).
- You have created a data federation channel and authorized an application to access data through the channel.

## Configuration Steps

1. From the channel list on the **Channel Manager** page, find the target channel, select **... > Get URL**, and copy the JDBC URL of the channel.

2. Download the data federation JDBC driver jar package from the maven repository to your local repository. The maven dependency is as per the below.

   ```
   <groupId>com.envisioniot</groupId>
   <artifactId>enos-datafederation-jdbc</artifactId>
   <version>0.0.1</version>
   ```

   <br />

3. Copy the JDBC driver jar package to the ``Drivers`` directory under the installation path of Tableau. The directories for different operating systems are as per the below.

   ```
   Windows：C:\Program Files\Tableau\Drivers
   Mac：~/Library/Tableau/Drivers
   Linux: /opt/tableau/tableau_driver/jdbc
   ```
   
   <br />
   
   For more information, see [Tableau Desktop and Web Authoring Help](https://help.tableau.com/current/pro/desktop/en-us/examples_otherdatabases_jdbc.htm).

   <br />

4. Run Tableau and click **Other Databases (JDBC)** on the **Connection** page.

   .. image:: ../../media/tableau_jdbc.png

   <br />

5. Complete the following settings for the data source connection.

   - **User**: Enter the access key of the application that is authorized by the data federation channel.
   - **Password**: Enter the secret key of the application. For information about getting the application access key and secret key, see [Registering and Managing Applications](/docs/app-development/en/dev/app_management/managing_apps.html).
   - **URL**: Enter the JDBC URL that was copied in step 1 and append the ``dbEscapeNeeded=false`` parameter at the end of the JDBC URL. For example, `jdbc:datafederation://{domain_name}/data-federation/v2.0/channels/read/{channel_id}?orgId={orgId}&dbEscapeNeeded=false`.

   <br />

   .. image:: ../../media/tableau_jdbc_setting.png

   <br />

6. Click **Log In** to connect to the data source. Drag and drop a data source table to load the data from the data source or transform the data as needed.

   .. image:: ../../media/tableau_jdbc_result.png

   <br />

7. You can also use custom SQL queries to generate data reports for data visualization, for example:

   ```
   select a.user_id, a.sex, a.age, a.province, b.invest_date, b.loan_name, b.invest_amount from mysql196.tableau.`user` a join mysql196.tableau.`trance` b on a.user_id=b.user_id
   ```

   .. image:: ../../media/tableau_jdbc_visualization.png


<!--end-->
