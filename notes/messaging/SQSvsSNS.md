
##  Amazon SQS vs SNS

| Feature            | Amazon SQS                                                     | Amazon SNS                                                |
|--------------------|----------------------------------------------------------------|-----------------------------------------------------------|
| **Type**           | Queue service                                                  | Notification service                                      |
| **Model**          | Pull-based                                                     | Push-based                                                |
| **Usage**          | Used for decoupling components of a cloud application          | Used for fan-out message delivery to multiple subscribers |
| **Throughput**     | Unlimited (Standard Queue), Limited (FIFO Queue)               | Unlimited                                                 |
| **Ordering**       | No (Standard Queue), Yes (FIFO Queue)                          | No (Standard Topic), Yes (FIFO Topic)                     |
| **Delivery Attempt** | Multiple attempts until the message is processed or the retention period expires | Single attempt for push notifications                 |
| **Message Filtering** | No native message filtering                                  | Message filtering with subscription filter policies       |
| **Fan Out Capability** | No direct fan out; consumers poll the messages               | Yes, supports direct fan out to multiple subscribers      |

## vs RabbitMQ

| Feature               | Amazon SQS                                     | Amazon SNS                                      | RabbitMQ                                    |
|-----------------------|------------------------------------------------|-------------------------------------------------|---------------------------------------------|
| **Type**              | Message queuing service                        | Pub/Sub messaging service                       | Message broker                              |
| **Message Model**     | Queue (Point-to-Point)                         | Topic (Publish/Subscribe)                       | Supports both Queue and Topic (Exchange)    |
| **Delivery Model**    | Pull-based (Consumers poll for messages)       | Push-based (Messages pushed to subscribers)     | Both Pull-based and Push-based              |
| **Main Use Case**     | Decoupling internal system components          | Broadcasting messages to multiple consumers     | Decoupling systems, work queues, routing    |
| **Throughput**        | High (Standard Queue), Controlled (FIFO Queue) | High                                            | High, configurable with various plugins    |
| **Ordering**          | FIFO ordering (FIFO Queues)                    | No inherent ordering                            | Ordering can be achieved with various types of exchanges |
| **Durability**        | Messages are stored until processed or timeout | Messages not stored (except for retries)        | Messages can be persistent or transient    |
| **Delivery Guarantee**| At least once (Standard Queue), Exactly once (FIFO Queue) | At least once                                | At least once, exactly once with confirmations |
| **Scalability**       | Managed by AWS, auto-scaling                   | Managed by AWS, auto-scaling                     | Manually managed, clustering for scalability|
| **Message Filtering** | Not supported                                  | Supported with subscription filter policies     | Supported with routing keys and bindings   |
| **Fan-out**           | Not directly supported (workarounds possible)  | Direct support with topics                      | Direct support using fanout exchange       |
| **Feature Analogies** | -                                               | -                                               | Exchange = SNS Topic, Queue = SQS Queue    |

