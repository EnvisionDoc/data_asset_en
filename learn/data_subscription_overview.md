# Data Subscription Overview

EnOS Data Subscription function improves the API calling efficiency of applications with active data push, which supports subscription to real-time asset data, and asset alert data.

Benefiting from the data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, the subscribed data will be pushed automatically, and applications can consume the pushed data as needed, thus improving API calling efficiency and reducing costs.

## Features

**Multiple data source subscription**

Data subscription service supports multiple data sources, including real-time asset data and asset alert data.

**Visualized configuration**

A GUI is available for you to customize the data subscription configuration, such as creating, configuring, starting, stopping, or deleting subscription jobs.

**Data subscription SDK**

Java SDK is provided for you to consume subscribed data in your applications.

For detailed information about creating data subscription jobs, see [Developing Data Subscription Jobs](../howto/obtain/managing_data_subscription).

## Advantages

- Decoupling data production and data consumption, enabling traffic control of the consumer.
- Rich set of data filtering conditions (organization, model, measuring point, and asset).
- Cross-organization data subscription (through purchasing applications of other organizations).
- Supporting "at-least-once" message delivery semantics, avoiding data loss.
- Supporting consumer groups. A topic can be consumed by multiple consumers (2 consumers are supported currently) in a same group at the same time, improving data consumption efficiency in case of huge data volume.  A topic can also be consumed by multiple consumer groups.
- Supporting resuming data consumption at breakpoint. Within 24 hours after the consumer client stops consuming data, the same consumer group can be used to continue consuming subscribed data from the breakpoint.
