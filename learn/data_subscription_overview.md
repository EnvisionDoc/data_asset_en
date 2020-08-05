# Data Subscription Overview

<br />

The EnOS Data Subscription service improves the performance of API calls with active data push, which supports the subscription to asset time series data (real-time and history data), asset alert data, and asset event data.

<br />

With this data subscription service, applications do not need to call APIs repeatedly and frequently to get asset data. Instead, the subscribed data will be pushed automatically, and applications can consume the pushed data as needed, thus improving API call performance and reducing costs.

<br />

The major components and architecture of the Data Subscription service is shown in the figure below.

<br />

.. image:: ../media/subscription_arch.png


## Features

<br />

**Multiple data source subscription**

The data subscription service supports multiple data sources, including time series data subscription, alert data subscription, and event data subscription.

<br />

**Visualized configuration**

A GUI is available for you to customize the data subscription configuration, such as creating, configuring, starting, stopping, or deleting subscription jobs.

<br />

**Data subscription SDK**

Java SDK, Python SDK, .NET SDK are provided for you to consume the subscribed data in your applications.

<br />

For detailed information about creating data subscription jobs, see [Developing Data Subscription Jobs](../howto/obtain/managing_data_subscription).

## Advantages

- Decoupling between data production and consumption, enabling client-side control.

- Rich set of data filtering conditions (organization, model, measurement point, and asset).

- Cross-organization data subscription (through purchasing applications of other organizations).

- Supporting "at-least-once" message delivery semantics, thus avoiding data loss.

- Monitoring the running statistics of data subscription jobs (producer rates, consumer rates, offset, and lag) to ensure that subscribed data is consumed in time without delay.

- Supporting consumer groups. A topic can be consumed by multiple consumers (2 consumers are supported currently) in a same group at the same time, improving data consumption efficiency in case of huge data volume. A topic can also be consumed by multiple consumer groups.

- Supporting the resuming of data consumption at breakpoint. Within 24 hours after the consumer client stops consuming data, the same consumer group can be used to continue consuming subscribed data from the breakpoint.
