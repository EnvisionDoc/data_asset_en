# Installing Calculator Libraries or Templates

<br />

Before developing stream processing jobs, you need to install the corresponding StreamSets calculator library or data calculation template.

## Prerequisites

- You are able to access the Stream Processing module.
- Your OU has requested for the **Stream Designing** resource type of the Stream Processing resources

## Installing Data Calculation Templates

1. Log in the **EnOS Management Console** and click **Stream Processing > Streamsets Libs**.

2. Click the **Template** tab to view the data calculation templates that can be installed. Currently, the following templates are available:

   - Time Window Aggregation: Supporting aggregation of numeric data for a single measurement point of a single device.
   - Electric Energy Cal by Meter Reading: Supporting calculation of daily electric energy by meter reading data.
   - Electric Energy Cal by Instant Power: Supporting calculation of daily electric energy by instant power data.
   - Electric Energy Cal by Average Power: Supporting calculation of daily electric energy by average power data.

   <br />

3. Find the template to be installed and click **Install**. The system will start the installation immediately.

   .. image:: ../../media/installing_stream_template.png


## Installing StreamSets Libraries

1. Log in the **EnOS Management Console** and click **Stream Processing > Streamsets Libs**.

2. Under the **Calculator Library** tab, view the StreamSets calculator libraries that can be installed.

3. Find the library to be installed and click **Install**. The system will start the installation immediately.

   .. image:: ../../media/installing_streamsets_lib.png


## Uninstalling Calculator Libraries or Templates

If your business does not need the installed calculator libraries or templates, or if you want to install a newer version, you can uninstall the libraries or templates to release the Stream Designing resource.

.. note:: Before uninstalling a calculator library or template, ensure that no stream processing job is still using the library or template.

<!--end-->
