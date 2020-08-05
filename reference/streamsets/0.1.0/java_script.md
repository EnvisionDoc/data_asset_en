# JavaScript

This stage supports the running of native JavaScripts to meet the requirements of custom business logic.

## Configuration

The configuration tabs for this stage are **General**, **Basic**, **Input/Output**, and **JavaScript**.

### General

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Name
     - Yes
     - The name of the stage.
   * - Description
     - No
     - The description of the stage.
   * - Stage Library
     - Yes
     - The streaming calculator library to which the stage belongs.
   * - Required Fields
     - No
     - The fields that the data records must contain. If the specified fields are not included, the record will be filtered out.
   * - Preconditions
     - No
     - The conditions that must be satisfied by the data records. Records that do not meet the conditions will be filtered out.
   * - On Record Error
     - Yes
     - The processing method for error data.

       + Discard: Error data will be discarded and ignored
       + Send to Error: Error messages will be reported
       + Stop Pipeline: The pipeline will be stopped


### Basic

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - IO Mapping Method
     - Yes
     - Select the mapping between the input and output points.

       + `1:1`: In each line of the Input/Output configuration, an input point corresponds to an output point.
       + `M:1`: In the Input/Output configuration, multiple input points correspond to one output point.

   * - Quality Filter
     - No
     - Filter the data according to the data quality. Only records that meet the quality conditions will be processed by this stage.


### Input/Output

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Input Point
     - Yes
     - Specify the input point of the records, using the format {modelId}::{pointId}. The `modelIdPath` and `pointId` of the input data must match with those of the input point.
   * - Output Point
     - No
     - Specify the output point of the records, using the format {modelId}::{pointId}. The `modelIdPath` and `pointId` of the output data processed by the JavaScript must match with those of the output point.


### JavaScript

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Name
     - Required?
     - Description
   * - Script
     - Yes
     - Enter the customized JavaScript, where `records` represents the input data that has been filtered by the quality conditions.

## Output Results

After running the customized script, the output results of this stage are included in the `attr` struct.


## Script Development Guide

In the Java Script, if there is calculation for data of Long type, such as sum, subtraction, multiplication, division, comparison, etc, you need to use ``parseFloat()`` to convert the data into Float type first. For example:

```
record.value['time'] = parseInt(parseFloat(record.value['time'])/60000) * 60000;
```

<br />

```
/**
 * Available constants:
 *   They are to assign a type to a field with a value null.
 *   NULL_BOOLEAN, NULL_CHAR, NULL_BYTE, NULL_SHORT, NULL_INTEGER, NULL_LONG
 *   NULL_FLOATNULL_DOUBLE, NULL_DATE, NULL_DATETIME, NULL_TIME, NULL_DECIMAL
 *   NULL_BYTE_ARRAY, NULL_STRING, NULL_LIST, NULL_MAP
 *
 * Available Objects:
 *
 *  records: an array of records to process, depending on the JavaScript processor
 *           processing mode it may have 1 record or all the records in the batch.
 *
 *  state: a dict that is preserved between invocations of this script.
 *        Useful for caching bits of data e.g. counters.
 *
 *  log.<loglevel>(msg, obj...): use instead of print to send log messages to the log4j log instead of stdout.
 *                               loglevel is any log4j level: e.g. info, error, warn, trace.
 *
 *  output.write(record): writes a record to processor output
 *
 *  error.write(record, message): sends a record to error
 *
 *  sdcFunctions.getFieldNull(Record, 'field path'): Receive a constant defined above
 *                            to check if the field is typed field with value null
 *  sdcFunctions.createRecord(String recordId): Creates a new record.
 *                            Pass a recordId to uniquely identify the record and include enough information to track down the record source.
 *  sdcFunctions.createMap(boolean listMap): Create a map for use as a field in a record.
 *                            Pass true to this function to create a list map (ordered map)
 *
 *  sdcFunctions.createEvent(String type, int version): Creates a new event.
 *                            Create new empty event with standard headers.
 *  sdcFunctions.toEvent(Record): Send event to event stream
 *                            Only events created with sdcFunctions.createEvent are supported.
 *  sdcFunctions.isPreview(): Determine if pipeline is in preview mode.
 *  
 * enosFunc.mcMin(Record,String pointID): Function for getting the minimum value of the measuring point;

 * enosFunc.mcMax(Record,String pointID): Function for getting the maximum value of the measuring point;

 * enosFunc.mcSum(Record,String pointID): Function for getting the sum of the values of the measuring point;

 * enosFunc.mcMean(Record,String pointID): Function for getting the average of the values of the measuring point;

 * enosFunc.mcCov(Record,String pointID): Function for getting the dispersion rate of the values of the measuring point;

 * enosFunc.input(Record,String pointID): Function for getting the value of the measuring point (supported data types are int、long、short、decimal、boolean、float、double);
 *
 * Available Record Header Variables:n *
 *  record.attributes: a map of record header attributes.
 *
 *  record.<header name>: get the value of 'header name'.
 */

// Sample JavaScript code
for(var i = 0; i < records.length; i++) {
  try {
    // Change record root field value to a STRING value
    //records[i].value = 'Hello ' + i;


    // Change record root field value to a MAP value and create an entry
    //records[i].value = { V : 'Hello' };

    // Access a MAP entry
    //records[i].value.X = records[i].value['V'] + ' World';

    // Modify a MAP entry
    //records[i].value.V = 5;

    // Create an ARRAY entry
    //records[i].value.A = ['Element 1', 'Element 2'];

    // Access a Array entry
    //records[i].value.B = records[i].value['A'][0];

    // Modify an existing ARRAY entry
    //records[i].value.A[0] = 100;

    // Assign a integer type to a field and value null
    // records[i].value.null_int = NULL_INTEGER

    // Check if the field is NULL_INTEGER. If so, assign a value
    // if(sdcFunctions.getFieldNull(records[i], '/null_int') == NULL_INTEGER)
    //    records[i].value.null_int = 123

    // Create a new record with map field
    // var newRecord = sdcFunctions.createRecord(records[i].sourceId + ':newRecordId');
    // newRecord.value = {'field1' : 'val1', 'field2' : 'val2'};
    // output.write(newRecord);
    // Create a new map and add it to the original record
    // var newMap = sdcFunctions.createMap(true);
    // newMap['key'] = 'value';
    // records[i].value['b'] = newMap;

    //Applies if the source uses WHOLE_FILE as data format
    //var input_stream = record.value['fileRef'].getInputStream();
    //try {
      //input_stream.read(); //Process the input stream
    //} finally{
      //input_stream.close()
    //}

    // Modify a header attribute entry
    // records[i].attributes['name'] = records[i].attributes['first_name'] + ' ' + records[i].attributes['last_name']    //

    // Get a record header with field names ex. get sourceId and errorCode
    // var sourceId = records[i].sourceId
    // var errorCode = ''
    // if(records[i].errorCode) {
    //     errorCode = records[i].errorCode
    // }

    // var record = records[i];
    // var targetPoint = 'pointId';
    // var minValue = enosFunc.mcMin(record,targetPoint);
    // var maxValue = enosFunc.mcMax(record,targetPoint);
    // var sumValue = enosFunc.mcSum(record,targetPoint);
    // var avgValue = enosFunc.mcMean(record,targetPoint);
    // var covValue = enosFunc.mcCov(record,targetPoint);
    // var inputValue = enosFunc.input(record,targetPoint);


    // Write record to processor output
    output.write(records[i]);
  } catch (e) {
    // Send record to error
    error.write(records[i], e);
  }
}

```
