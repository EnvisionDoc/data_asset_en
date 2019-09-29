# Data Subscription

EnOS Data Subscription function improves the API calling efficiency of applications with active data push, which supports subscription to real-time asset data, and asset alert data.

Benefiting from the data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, the subscribed data will be pushed automatically, and applications can consume the pushed data as needed, thus improving API calling efficiency and reducing costs.

## Features

**Multiple data source subscription**:

Data subscription service supports multiple data sources such as real-time asset data, asset alert data, etc.

**Visualized configuration**

A GUI is available for you to customize the data subscription configuration, such as creating, configuring, starting, stopping, or deleting subscription jobs.

**Data subscription SDK**

Java SDK is provided for you to consume subscribed data in your applications.

For detailed information about creating data subscription jobs, see [Developing Data Subscription Jobs](/docs/data-asset/en/2.0.8/howto/obtain/managing_data_subscription.html).

## Advantages

- Decoupling data production and data consumption.
- Rich set of data filtering conditions (organization, model, measuring point, and asset).
- Cross-organization data subscription (through service account).
- Supporting "at-least-once" message delivery semantics.
- "Pulling subscribed data" consumption model, supporting traffic control of the consumer.
- Supporting consumer groups (a topic can be consumed by multiple consumers repeatedly).
