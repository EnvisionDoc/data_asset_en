# Data Subscription SDK Reference

## For Real-time Data Subscription

### Subscription Client Class: EosClient

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - EosClient(String host, Integer port, String accessKey, String secretKey)
     - The constructor function.
     - + host: The subscription service host.
       + port
       + accessKey
       + secretKey: The secret of the accessKey.
     - EosClient instance
   * - getDataService()
     - Get the real-time data subscription service instance.
     - N/A
     - IDataService instance

### Real-time Data Subscription Service Class: IDataService

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - subscribe(IDataHandler dataHandler, String subId)
     - Get the subscribed real-time data of subID (this subscription client belongs to the default consumer group).
     - + dataHandler: The data processing object.
       + subId: The subscription ID.
     - null
   * - subscribe(IDataHandler dataHandler, String subId, String consumerGroup)
     - Get the subscribed real-time data of the subID and define the consumer group.

       + The "consumerGroup" parameter specifies the consumer group of the current client.
       + The clients in a same group can process subscribed data together, which improves the capability of data processing.
       + A message can be consumed by only 1 client in a consumer group.

     - + dataHandler: The real-time data processing object.
       + subId: The subscription ID.
       + consumerGroup: The consumer group (if null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the "consumerGroup" value).
     - null

### Real-time Data Handling Class: IDataHandler

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - dataRead(StreamMessage message)
     - Read the subscribed real-time data.
     - message: The subscribed real-time data.
     - null


## For Alert Data Subscription

### Subscription Client Class: EosClient

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - EosClient(String host, Integer port, String accessKey, String secretKey)
     - The constructor function.
     - + host: The subscription service host.
       + port
       + accessKey
       + secretKey: The secret of the accessKey.
     - EosClient instance
   * - getAlertService()
     - Get alert data subscription service instance.
     - N/A
     - IAlertService instance


### Alert Data Subscription Service Class: IAlertService

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - subscribe(IAlertHandler alertHandler, String subId)
     - Get the subscribed alert data of the subID (this subscription client belongs to the default consumer group).
     - + alertHandler: The data processing object.
       + subId: The subscription ID.
     - null
   * - subscribe(IAlertHandler alertHandler, String subId, String consumerGroup)
     - Get the subscribed alert data of the subID and define the consumer group.

       + The "consumerGroup" parameter specifies the consumer group of the current client.
       + The clients in a same group can process subscribed data together, which improves the capability of data processing.
       + A message can be consumed by only 1 client in a consumer group.

     - + alertHandler: The alert data processing object.
       + subId: The subscription ID.
       + consumerGroup: The consumer group (if null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the "consumerGroup" value).
     - null


### Alert Data Handling Class: IAlertHandler

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - alertRead(Alert alert)
     - Read the subscribed alert data.
     - alert: The subscribed alert data.
     - null


## For Offline Data Subscription

### Subscription Client Class: EosClient

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - EosClient(String host, Integer port, String accessKey, String secretKey)
     - The constructor function.
     - + host: The subscription service host.
       + port
       + accessKey
       + secretKey: The secret of the accessKey.
     - EosClient instance
   * - getOfflineDataService()
     - Get the offline data subscription service instance.
     - N/A
     - IDataService instance

### Offline Data Subscription Service Class: IDataService

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - subscribe(IDataHandler dataHandler, String subId)
     - Get the subscribed offline data of the subID (this subscription client belongs to the default consumer group).
     - + dataHandler: The data processing object.
       + subId: The subscription ID.
     - null
   * - subscribe(IDataHandler dataHandler, String subId, String consumerGroup)
     - Get subscribed offline data of subID and define the consumer group.

       + The "consumerGroup" parameter specifies the consumer group of the current client.
       + The clients in a same group can process subscribed data together, which improves the capability of data processing.
       + A message can be consumed by only 1 client in a consumer group.

     - + dataHandler: The offline data processing object.
       + subId: The subscription ID.
       + consumerGroup: The consumer group (if null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the "consumerGroup" value).
     - null

### Offline Data Handling Class: IDataHandler

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - dataRead(StreamMessage message)
     - Read the subscribed offline data.
     - message: The subscribed offline data.
     - null

## For Event Data Subscription

### Subscription Client Class: EosClient

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - EosClient(String host, Integer port, String accessKey, String secretKey)
     - The constructor function.
     - + host: The subscription service host.
       + port
       + accessKey
       + secretKey: The secret of the accessKey.
     - EosClient instance
   * - getEventService()
     - Get event data subscription service instance.
     - N/A
     - IEventService instance


### Event Data Subscription Service Class: IEventService

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - subscribe(IEventHandler eventHandler, String subId)
     - Get the subscribed event data of the subID (this subscription client belongs to the default consumer group).
     - + eventHandler: The data processing object.
       + subId: The subscription ID.
     - null
   * - subscribe(IEventHandler eventHandler, String subId, String consumerGroup)
     - Get the subscribed event data of the subID and define the consumer group.

       + The "consumerGroup" parameter specifies the consumer group of the current client.
       + The clients in a same group can process subscribed data together, which improves the capability of data processing.
       + A message can be consumed by only 1 client in a consumer group.

     - + eventHandler: The event data processing object.
       + subId: The subscription ID.
       + consumerGroup: The consumer group (if null is specified, the system uses "DefaultConsumerGroup" by default. If you specify a value manually, avoid using "DefaultConsumerGroup" as the "consumerGroup" value).
     - null

### Event Data Handling Class: IEventHandler

.. list-table::
   :widths: 20 40 30 10
   :header-rows: 1

   * - Function
     - Description
     - Parameter
     - Response
   * - eventRead(Event event)
     - Read the subscribed event data.
     - event: The subscribed event data.
     - null

<!--end-->
