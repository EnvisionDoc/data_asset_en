# Consuming Subscribed Data

<br />

After the data subscription job starts running, you can use the data subscription SDK (Java or Python) to develop applications and consume the subscribed data. This topic shows how to install the data subscription SDK and provides code samples for consuming the subscribed data.

## For Java SDK

The steps for installing the Java SDK and consuming the subscribed data are as follows.

### Installing Data Subscription SDK for Java

Get the Maven dependency information of the data subscription SDK and add it to your development project.

1. Open the Maven repository of the SDK at <https://mvnrepository.com/artifact/com.envisioniot/enos-subscribe>.

2. Open your development environment, and add the maven dependency for the SDK in your Java project. See the following example.

   ```
   <dependency>
     <groupId>com.envisioniot</groupId>
     <artifactId>enos-subscribe</artifactId>
     <version>2.5.0</version>
   </dependency>
   <dependency>
     <groupId>com.google.code.gson</groupId>
     <artifactId>gson</artifactId>
     <version>2.8.0</version>
   </dependency>
   <dependency>
     <groupId>log4j</groupId>
     <artifactId>log4j</artifactId>
     <version>1.2.16</version>
   </dependency>
   ```



### Code Sample for Consuming the Subscribed Real-time Data

The following code sample is for consuming the subscribed asset real-time data with a specified consumer group. In case of huge data volume, you can run 2 consumer clients of the same consumer group to improve the data consumption efficiency.


```
import com.envisioniot.sub.client.EosClient;
import com.envisioniot.sub.client.data.IDataHandler;
import com.envisioniot.sub.client.data.IDataService;
import com.envisioniot.sub.common.model.dto.StreamMessage;

public class DataServiceDemo {
    public static void main(String[] args) throws Exception {
        // Host of the data subscription service
        String host = "subscription_server";
        // Port of the data subscription service
        int port = 9001;
        // APP authentication (Generated when registering your APP)
        String accessKey = "access_key";
        // APP authentication
        String secretKey = "secret_key";

        // Subscription ID
        String subId = "subscription_id";

        // Consumer group name
        String consumerGroup = "consumer_group";

        EosClient eosClient = new EosClient(host, port, accessKey, secretKey);

        // Get the real-time data service
        IDataService dataService = eosClient.getDataService();

        // Create the data handler function
        IDataHandler dataHandler = new IDataHandler(){
            public void dataRead(StreamMessage message) {
                System.out.println(message);
            }
        };

        // Establish connection with subscription ID and consumer group
        dataService.subscribe(dataHandler, subId, consumerGroup);
    }
}
```

.. note:: - The `host` and `port` of the subscription server will vary with the cloud region and instance. To get the address and port of the subscription service for your cloud instance, log in to the **EnOS Management Console** and select **Help > Environment Information**.
      - Each subscription topic has 2 partitions. That is, each topic allows at most 2 data consumers at the same time.
      - Currently, a data consumer can consume 1 topic only.
      - By default, data is stored in the topic for 3 days.

### Code Sample for Consuming the Subscribed Alert Data

The following code sample is for consuming the subscribed asset alert data with the default consumer group.

```
import com.envisioniot.sub.client.EosClient;
import com.envisioniot.sub.client.event.IAlertHandler;
import com.envisioniot.sub.client.event.IAlertService;
import com.envisioniot.sub.common.model.Alert;

public class AlertServiceDemo1 {
    public static void main(String[] args) throws Exception {
        // Host of the data subscription service
        String host = "subscription_server";
        // Port of the data subscription service
        int port = 9001;
        // APP authentication (Generated when registering your APP)
        String accessKey = "access_key";
        // APP authentication
        String secretKey = "secret_key";

        // Subscription ID
        String subId = "subscription_id";

        EosClient eosClient = new EosClient(host, port, accessKey, secretKey);

        // Get the alert data service
        IAlertService alertService = eosClient.getAlertService();

        // Create the data handler function
        IAlertHandler alertHandler = new IAlertHandler (){
            @Override
            public void alertRead(Alert alert) {
                System.out.println(alert);
            }
        };

        // Establish connection with subscription ID
        alertService.subscribe(alertHandler, subId);
    }
}
```

### Code Sample for Consuming the Subscribed Offline Data

The following code sample is for consuming the subscribed asset offline data with the default consumer group.

```
import com.envisioniot.sub.client.EosClient;
import com.envisioniot.sub.client.data.IDataHandler;
import com.envisioniot.sub.client.data.IDataService;
import com.envisioniot.sub.common.model.dto.StreamMessage;

public class DataServiceDemo {
    public static void main(String[] args) throws Exception {
        // Host of the data subscription service
        String host = "subscription_server";
        // Port of the data subscription service
        int port = 9001;
        // APP authentication (Generated when registering your APP)
        String accessKey = "access_key";
        // APP authentication
        String secretKey = "secret_key";

        // Subscription ID
        String subId = "subscription_id";

        EosClient eosClient = new EosClient(host, port, accessKey, secretKey);

        // Get the real-time data service
        IDataService dataService = eosClient.getOfflineDataService();

        // Create the data handler function
        IDataHandler dataHandler = new IDataHandler(){
            public void dataRead(StreamMessage message) {
                System.out.println(message);
            }
        };

        // Establish connection with subscription ID
        dataService.subscribe(dataHandler, subId);
    }
}
```


### Code Sample for Consuming the Subscribed Event Data

The following code sample is for consuming the subscribed asset event data with the default consumer group.

```
import com.envisioniot.sub.client.EosClient;
import com.envisioniot.sub.client.event.IAlertHandler;
import com.envisioniot.sub.client.event.IAlertService;
import com.envisioniot.sub.common.model.Alert;

public class AlertServiceDemo1 {
    public static void main(String[] args) throws Exception {
        // Host of the data subscription service
        String host = "subscription_server";
        // Port of the data subscription service
        int port = 9001;
        // APP authentication (Generated when registering your APP)
        String accessKey = "access_key";
        // APP authentication
        String secretKey = "secret_key";

        // Subscription ID
        String subId = "subscription_id";

        EosClient eosClient = new EosClient(host, port, accessKey, secretKey);

        // Get the event data service
        IEventService eventService = eosClient.getEventService();

        // Create the data handler function
        IEventHandler eventHandler = new IEventHandler (){
            @Override
            public void eventRead(Event event) {
                System.out.println(event);
            }
        };

        // Establish connection with subscription ID
        eventService.subscribe(eventHandler, subId);
    }
}
```


## |update| For Python SDK

The steps for installing the Python SDK and consuming the subscribed data are as follows.

### Installing Data Subscription SDK for Python

The Data Subscription SDK for Python supports Python 2.7, Python 3.4, and newer versions.

1. Install the following dependency modules.

   - six
   - google.protobuf
   - websocket_client

2. Open the GitHub repository of the SDK to download the installation code: https://github.com/EnvisionIot/enos-subscription-service-sdk-python

3. (Optional) Install the Data Subscription SDK for Python with pip.

```
pip install enos-subscribe
```

### Code Sample for Consuming the Subscribed Real-time Data

The following code sample is for consuming the subscribed asset real-time data with the Data Subscription SDK for Python.

```
if __name__ == '__main__':
    client = DataClient(host='Host of the subscription server', port='9001',
                        access_key='Access key of your APP',
                        access_secret='Secret key of your APP')

    client.subscribe(sub_id='ID of the subscription job')

    for message in client:
        print(message)
```

.. note:: - The `host` and `port` of the subscription server will vary with the cloud region and instance. To get the address and port of the subscription service for your cloud instance, log in EnOS Management Console and select **Help > Environment Information**.
      - By default, data is stored in the Kafka topic for 3 days.


### Code Sample for Consuming the Subscribed Alert Data

The following code sample is for consuming the subscribed asset alert data with the Data Subscription SDK for Python.

```
if __name__ == '__main__':
    client = AlertClient(host='Host of the subscription server', port='9001',
                        access_key='Access key of your APP',
                        access_secret='Secret key of your APP')

    client.subscribe(sub_id='ID of the subscription job')

    for message in client:
        print(message)
```

### Code Sample for Consuming the Subscribed Offline Data

The following code sample is for consuming the subscribed asset offline data with the Data Subscription SDK for Python.

```
if __name__ == '__main__':
    client = OfflineDataClient(host='Host of the subscription server', port='9001',
                        access_key='Access key of your APP',
                        access_secret='Secret key of your APP')

    client.subscribe(sub_id='ID of the subscription job')

    for message in client:
        print(message)
```

### Code Sample for Consuming the Subscribed Event Data

The following code sample is for consuming the subscribed asset event data with the Data Subscription SDK for Python.

```
from enos_subscribe import EventClient

if __name__ == '__main__':
    client = EventClient(host='sub-host', port='sub-port',
                        access_key='Your Access Key of this subscription',
                        access_secret='Your Access Secret of this subscription')

    client.subscribe(sub_id='Your subscription Id')

    for message in client:
        print(message)

```


## Monitoring the Running Statistics of Data Subscription Jobs

When a huge volume of data is being subscribed to, you can check the running statistics of the data subscription job to ensure that the subscribed data is consumed in time.

1. Log in to the **EnOS Management Console** and open the Data Subscription page. From the **Operations** column of the data subscription job list, select **More (..) > Running Statistics**.

2. In the pop-up window, you can view the producer rates and consumer rates of the data subscription job, and see whether there is any delay of data consumption (by comparing the data producer rates with the data consumer rates).

   .. image:: ../../media/subscription_statistics.png

   .. note:: In the above example, *Producer Rates* shows the speed of data production from the real-time data channel, and *Consumer Rates* shows the speed of data consumption by each consumer group. The *offset* line and number indicate the total volume of subscribed data by the subscription job. The consumer group lines and number indicate the volume of subscribed data that has not been consumed by the consumer group.

<br />

If there is a delay in data consumption, you can run 2 consumer clients of the same consumer group to improve the data consumption efficiency.

.. |update| image:: ../../media/2_1_update.png
   :width: 80px

<!--end-->
