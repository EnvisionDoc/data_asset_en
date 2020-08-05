# Registering a GitLab Data Source

<br />

Before synchronizing data from a GitLab project (e.g. for deploying algorithm models), you need to register the data source to configure the connection information of the GitLab server.

<br />

This section shows the steps to register a GitLab data source in EnOS.

## Procedure

1. In the **EnOS Management Console**, click **Data Source Registration** from the left navigation menu.

2. Click **Add Data Source**.

3. In the **Data Sources** window, provide information for the following.

   - **Data source**: Enter a name for the data source. The maximum length is 50 characters and can be a combination of the following characters.
     - a through z
     - A through Z
     - 0 through 9
     - _ (underscore)  

     <br />

   - **Data Source Type**: Select GitLab.
   - **Token**: Enter the access token for accessing the GitLab repository. The steps for getting the access token are as per the below.
     - Log in to the GitLab project, click the **User** drop-down list in the upper right corner, and select **Settings**.
     - On the **User Settings** page, select **Access Tokens** from the left navigation bar.
     - Enter a name for the access token to be created, select an expiring date, select the `api`, `read_user`, `read_repository` permission options, and click **Create personal access token**.
     - In the **Your New Personal Access Token** field, copy the generated access token.

     <br />

   - **Git URL**: Enter the URL of the GitLab project, using the format `http://hostname:port/namespace/project`.
   - **Data Source Description**: Enter a description for the data source.

   <br />

4. Click **Test** to test the data source connection.

   <!-- >.. image:: ../media/gitlab_connection.png
      :width: 400px -->

5. Click **OK** to save the configuration.

## Results

The data source will be shown in the **Data Source Registration** table.


## Next Step

When the connection is successfully established, you can add files from the GitLab project for deploying and hosting algorithm models. For more information, see [Deploying an Algorithm Model](/docs/offline-data/en/dev/model_deployment/configuring_deployment.html).
