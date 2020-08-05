# Preparing Data Exploring Environment

<br />

Before using the Data Sandbox Service with Zeppelin Notebook and Jupyter Notebook, you need to request the Data Sandbox resource on the EnOS Management Console.


## Requesting for the Sandbox Resource

1. Log in to the **EnOS Management Console** with an OU administrator account and click **Resource Management > Resource List** from the left navigation menu.

2. Under the **Enterprise Data Platform** tab, click the **Request Resource** button for **Data Sandbox** resource.

3. Enter the sandbox name, select the appropriate CPU, memory, and storage based on business needs, and click the **Request** button.

   .. image:: media/sandbox.png
      :width: 400px

<br />

After the sandbox resource request is approved, and the status of the request becomes to *Allocated*, you can start using the Data Sandbox Service.

## Managing the Sandbox Resource

After the Data Sandbox resource is allocated, select **Batch Processing > Data Sandbox** from the left navigation menu in the **EnOS Management Console**. Find the requested sandbox and click the **Start** icon from the **Operations** column. When the status of the sandbox becomes *Running*, you can click Zeppeline or Jupyter in the **URL** column to open the corresponding notebook.

<br />

If you do not need to use the data sandbox resource, you can click the **Stop** icon in the **Operations** column to stop the sandbox. When the sandbox is stopped, delete the requested sandbox resource on the **Resource Management** page on the **EnOS Management Console**.

<!--end-->
