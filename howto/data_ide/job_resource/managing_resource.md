# Managing Resources

<br />

After a resource is created, you can manage the different versions of the resource by performing tasks such as updating, deleting, and downloading.

<br />

To manage a resource, double-click the resource from the resource directory tree to show the resource information panel.

## Updating a Resource

When a resource is updated, the tasks that reference the resource are automatically updated.

- To update its generic information such as the resource name and description, click **Edit Resource**.

- To update a resource version, click **Update** from the **Operations** column. Upload the new resource bundle, and modify the version number and description according to your needs.

## Tracing Workflows that Reference a Resource Version

To trace the usage of a resource version, you can view the workflows and task nodes that reference the resource by clicking **Reference** from the **Operations** column.

## Deleting a Resource Version or Entire Resource

You can delete a resource version or an entire resource when it is no longer needed.

.. note:: The following rules apply when you delete a resource or a resource version.

  - Before deleting a resource version, ensure that the version of the resource is not referenced by any workflows. Otherwise, the current resource version cannot be deleted. To determine which workflow or task node is referencing the resource version, click **Reference** from the **Operations** column.

  - Before deleting an entire resource, you must first delete all the versions under the resource. Otherwise, you cannot delete the entire resource.

- To delete a resource version, click **Delete** from the **Operations** column.

- To delete an entire resource, right-click the resource from the directory tree and click **Delete** from the menu.


## Downloading a Resource Version

You may want to download a resource file for redevelopment. To download a resource file to your local system, click the file name from the **Resource File** column.
