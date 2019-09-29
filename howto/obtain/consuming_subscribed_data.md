# Consuming Subscribed Data

After the data subscription job starts running, you can use the data subscription SDK to develop applications and consume the subscribed data. This topic introduces installation method of data subscription SDK and provides code samples for consuming subscribed data.

## Installing Data Subscription SDK

Get the Maven dependency information of the data subscription SDK and add it to your development project. Detailed steps are as follows:

1. Open the Maven repository of the SDK at <https://mvnrepository.com/artifact/com.envisioniot/enos-subscribe/2.2.0>.

2. Open your development environment, add the maven dependency for the SDK in your Java project. See the following example.

   ```
   <dependency>
     <groupId>com.envisioniot</groupId>
     <artifactId>enos-subscribe</artifactId>
     <version>2.2.0</version>
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



## Code Sample for Consuming Subscribed Real-time Data

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

        // Subscription group (Optional)
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

        // Establish connection with subscription ID
        dataService.subscribe(dataHandler, subId);

        // Optionally, establish connection with subscription ID and consumer group
        dataService.subscribe(dataHandler, subId, consumerGroup);
    }
}
```

.. note:: - The `host` and `port` of the subscription server vary with the cloud region and instance. For private cloud instances, contact your Envision project manager or support representative to get the host and port information.
      - Each subscription topic has 2 partitions. That is, each topic allows at most 2 data consumers at the same time.
      - Currently, a data consumer can consume 1 topic only.
      - By default, data is stored in the topic for 3 days.

## Code Sample for Consuming Subscribed Alert Data

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

        // Subscription group (Optional)
        String consumerGroup = "consumer_group";

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

        // Optionally, establish connection with subscription ID and consumer group
        alertService.subscribe(alertHandler, subId, consumerGroup);
    }
}
```



<!--end-->
