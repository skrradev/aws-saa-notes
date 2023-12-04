# Kinesis

```mermaid
graph LR
    A[Amazon Kinesis Overview] -->|For real-time data streams| B[Kinesis Data Streams]
    A -->|Load streaming data into AWS data stores| C[Kinesis Data Firehose]
    A -->|Real-time analytics on streaming data| D[Kinesis Data Analytics]
    A -->|Capture, process, and store video streams| E[Kinesis Video Streams]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef datastream fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef firehose fill:#ddf,stroke:#333,stroke-width:2px;
    classDef analytics fill:#ff9,stroke:#333,stroke-width:2px;
    classDef videostream fill:#f96,stroke:#333,stroke-width:2px;

    class B datastream;
    class C firehose;
    class D analytics;
    class E videostream;



```

## Kinesis Data Streams

```mermaid
graph LR
A[Producers] -->|Generate and push data| B[Kinesis Data Streams]
B -->|Consists of| C[Shards]
B -->|Holds and processes data| D[Record]
C -->|Support up to 1 MB/sec or 1000 messages/sec| E[Shard Capacity]
B -->|Distributed to| F[Consumers]
F -->|Process data| G[Kinesis Client Library KCL/AWS SDK]
F -->|Load data into AWS data stores| H[Kinesis Data Firehose]
F -->|Real-time processing with SQL or Apache Flink| I[Kinesis Data Analytics]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef streams fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef shard fill:#ddf,stroke:#333,stroke-width:2px;
    classDef consumer fill:#ff9,stroke:#333,stroke-width:2px;
    
    class A,B default;
    class C shard;
    class D,E streams;
    class F consumer;
    class G,H,I consumer;

```


```mermaid
graph LR
    A[Kinesis Data Streams] -->|Retention period of 24h to 365 days| B[Data Retention]
    A -->|Ability to reprocess data| C[Data Reprocessing]
    A -->|Data cannot be deleted| D[Immutability]
    A -->|Partition keys direct data to shards| E[Partition Keys and Ordering]
    A -->|Entities that put data into the stream| F[Producers]
    F -->|Examples: Server Logs, IoT Devices, Application Data| G[Producer Examples]
    A -->|Applications or services processing data| H[Consumers]
    H -->|Examples: KCL Applications, AWS Lambda, Kinesis Data Firehose, Kinesis Data Analytics| I[Consumer Examples]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef feature fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef example fill:#ddf,stroke:#333,stroke-width:2px;

    class A default;
    class B,C,D,E,F,H feature;
    class G,I example;

```
## Kinesis Data Streams Capacity Modes
```mermaid
graph LR
A[Amazon Kinesis Data Streams Capacity Modes] --> B[Provisioned Mode]
B -->|Fixed number of shards| C[Shard Capacity: 1MB/s in, 2MB/s out]
B -->|Pay per shard provisioned| D[Cost: Fixed, calculated hourly]

    A --> E[On-demand Mode]
    E -->|Scales automatically based on peak usage| F[Default: 4MB/s in or 4000 records/s]
    E -->|Pay per stream per hour and data in/out| G[Cost: Based on data ingested/egressed]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef mode fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef detail fill:#ddf,stroke:#333,stroke-width:2px;
    
    class A default;
    class B,E mode;
    class C,D,F,G detail;
```

## Kinesis Data Streams Capacity Modes Comparison

| Feature | Provisioned Mode | On-demand Mode |
|---------|------------------|----------------|
| **Capacity Planning** | Must manually provision and manage the number of shards. | Automatic scaling without the need to manage shard capacity. |
| **Throughput** | 1 MB/s or 1000 messages/s for data input per shard; 2 MB/s for data output per shard (classic or enhanced fan-out consumer). | Default capacity provisioned (4 MB/s in or 4000 records per second) scales automatically. |
| **Scaling** | Manual scaling through the AWS Management Console or Kinesis API. | Scales automatically based on observed throughput peak during the last 30 days. |
| **Billing** | Pay per shard provisioned per hour. | Pay per stream per hour & data in/out per GB. |
| **Shard Management** | You choose the number of shards provisioned, scale manually or using API. | No need to provision or manage the capacity. |

## Kinesis Data Streams Security

```mermaid
graph LR
    A[Kinesis Data Streams Security] --> B[Access Control]
    B --> C[IAM Policies for Stream Access]
    A --> D[Encryption In-Transit]
    D --> E[HTTPS for Secure Data Transfer]
    A --> F[Encryption At Rest]
    F --> G[AWS KMS Keys for Data Protection]
    A --> H[Client-Side Encryption]
    H --> I[Option for Client-Managed Encryption/Decryption]
    A --> J[VPC Endpoints]
    J --> K[Private Connection within Amazon VPC]
    A --> L[Monitoring with CloudTrail]
    L --> M[Audit & Log API Calls]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,D,F,H,J,L subheading;
    class C,E,G,I,K,M details;
```

## Kinesis Data Streams vs Apache Kafka

| Feature                        | Kinesis Data Streams                                        | Apache Kafka                                                |
|--------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|
| **Managed Service**            | AWS managed service with integrated AWS support.            | Self-managed, although managed services like Confluent exist.|
| **Provisioning**               | Automatic scaling with shard splitting and merging.          | Manual partition management and scaling.                     |
| **Data Retention**             | Default retention of 24 hours, extendable up to 7 days.      | Configurable, default is 7 days, but can be set indefinitely.|
| **Throughput**                 | Throughput is determined by the number of shards.            | Throughput is determined by the number of partitions.        |
| **Ordering**                   | Ordered at the shard level.                                  | Ordered within partitions.                                   |
| **Data Durability**            | Replicated across three availability zones.                  | Replicated across broker nodes, configurable replication.    |
| **Security**                   | Integrated with AWS IAM, KMS for encryption.                 | Supports SSL/TLS, SASL for security.                         |
| **Serverless**                 | Offers a serverless option with Kinesis Data Streams.        | Kafka does not have a serverless option natively.            |
| **Message Size**               | Maximum payload size of 1MB per record.                      | Maximum message size is configurable, typically a few MB.    |
| **Real-time Processing**       | Offers Kinesis Data Analytics for real-time analytics.       | Kafka Streams API for real-time stream processing.           |
| **Integration**                | Deep integration with AWS ecosystem.                         | Broad integration with many third-party systems.             |
| **Client Libraries**           | AWS SDK, Kinesis Producer Library (KPL), Kinesis Client Lib. | Kafka Producer and Consumer APIs, Kafka Streams, Kafka Connect.|
| **Deployment**                 | Cloud-only on AWS infrastructure.                            | Can be deployed on-premises, in the cloud, or hybrid.        |
| **Pricing**                    | Pay for the throughput capacity and data processed.          | Free and open-source; costs associated with self-hosting or managed services.|
| **Use Case**                   | Ideal for AWS-centric applications and workloads.            | Suited for high-throughput, fault-tolerant applications.     |

## Kinesis Data Firehose

```mermaid
graph LR
    A[Producers] -->|Send data streams| B[Kinesis Data Firehose]
    A -->|Types: Applications, Clients, AWS Services| X[Producer Types]
    X -->|Producer Examples Examples:| Y[ IoT Devices \n, Logs, Metrics\n, Web Applications\n, Mobile Apps\n, Data Sensors\n, Kinesis Data Streams\n]
    B -->|Optional transformation| C[AWS Lambda Function]
    B -->|Batch writes to optimize throughput| D[Batch Writes]
    B -->|Loads data into| E[Destinations]
    E -->|Amazon S3, Redshift, Elasticsearch, etc.| F[Storage/Analytics Services]
    E -->|Custom HTTP Endpoints, Splunk, etc.| G[Third-Party Services]
    B -->|Backup for all or failed data| H[S3 Backup Bucket]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef producer fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef firehose fill:#ddf,stroke:#333,stroke-width:2px;
    classDef lambda fill:#ff9,stroke:#333,stroke-width:2px;
    classDef destination fill:#f96,stroke:#333,stroke-width:2px;
    classDef backup fill:#e6f7ff,stroke:#333,stroke-width:2px;

    class A producer;
    class B firehose;
    class C lambda;
    class D,E default;
    class F,G destination;
    class H backup;
    class X,Y producer;


```

## Kinesis Data Firehose Overview

```mermaid
graph LR
A[Kinesis Data Firehose Overview] --> B[Fully Managed Service]
B -->|Automatic scaling, Serverless| C[No Administration]
A -->|Integration with AWS and third-party services| D[Destinations]
D -->|Redshift, S3, Elasticsearch, Splunk, etc.| E[Service Integrations]
A -->|Based on data volume| F[Cost]
A -->|Near real-time, minimum 60s latency for non-full batches| G[Performance]
A -->|Supports various data formats and transformations| H[Data Formats]
H -->|Compression and conversions| I[Efficient Transfer]
A -->|Custom transformations with AWS Lambda| J[Data Transformation]
A -->|Backup failed or all data to S3| K[Backup]
K -->|Durability and recovery| L[Backup S3 Bucket]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef feature fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef detail fill:#ddf,stroke:#333,stroke-width:2px;
    
    class A default;
    class B,D,F,G,H,J,K feature;
    class C,E,I,L detail;
```

## Kinesis Data Streams vs Kinesis Data Firehose

```mermaid

graph LR
A[Kinesis Data Streams vs Kinesis Data Firehose] --> B[Kinesis Data Streams]
B -->|Real-time data ingestion at scale| C[Purpose]
B -->|Custom processing applications| D[Custom Code]
B -->|Approximately 200 milliseconds| E[Latency]
B -->|Manual scaling of shards| F[Scaling]
B -->|1 to 365 days retention| G[Data Storage Duration]
B -->|Replay or reprocess data| H[Replay Feature]

    A --> I[Kinesis Data Firehose]
    I -->|Load data into AWS services or HTTP endpoints| J[Purpose]
    I -->|Fully managed, no administration| K[Management]
    I -->|Minimum 60 seconds buffer time| L[Latency]
    I -->|Scales automatically with throughput| M[Scaling]
    I -->|Direct data delivery, no storage| N[Data Storage]
    I -->|One-time delivery, no replay| O[Replay Feature]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,I subheading;
    class C,D,E,F,G,H,J,K,L,M,N,O details;
```



| Feature                 | Kinesis Data Streams                          | Kinesis Data Firehose                          |
|-------------------------|----------------------------------------------|-----------------------------------------------|
| **Service Type**        | Real-time data streaming service             | Managed service for loading streaming data    |
| **Customization**       | Write custom code for producers/consumers     | No custom consumer code; direct to destination|
| **Latency**             | Provides real-time processing with latencies of approximately 200 milliseconds.              | Near real-time with a minimum buffer time of 60 seconds for data delivery               |
| **Management**          | Manual scaling (shard management)            | Fully managed, automatic scaling              |
| **Data Storage**        | 1 to 365 days retention                      | No data storage; direct delivery              |
| **Data Replay**         | Supports replaying data                      | No replay capability                          |
| **Use Case**            | Real-time processing, analytics              | Simplified data delivery to AWS/endpoints     |

## Data Ordering in Kinesis Data Streams

```mermaid
graph LR
    A[Data Ordering in Kinesis Data Streams] --> B[Scenario Description]
    B -->|Fleet of trucks sending GPS data| C[100 Trucks]
    A --> D[Data Consumption Requirement]
    D -->|Need to track each truck's movement accurately| E[Orderly Data Consumption]
    A --> F[Solution to Ordering]
    F -->|Use 'truck_id' as Partition Key| G[Partition Key Usage]
    A --> H[Shards in Kinesis Stream]
    H -->|Data distributed into multiple shards| I[Example: 3 Shards]
    A --> J[Partition Key Role]
    J -->|Ensures data order per truck| K[Order Preservation]
    A --> L[Visual Representations]
    L -->|Different colors/patterns for trucks and shards| M[Visualization of Data Flow]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,D,F,H,J,L subheading;
    class C,E,G,I,K,M details;
```

## SQS Ordering: Standard vs FIFO Queues
```mermaid
graph TD
    A[SQS Ordering: Standard vs FIFO Queues] --> B[SQS Standard Queues]
    B --> C[No Order Guarantee]
    C -->|Messages delivered in different order| D[Random Order Delivery]

    A --> E[SQS FIFO Queues]
    E --> F[Ordered Message Delivery]
    F -->|Messages kept in sent order| G[Strict Order]

    E --> H[Use of Group ID in FIFO]
    H -->|Allows concurrent processing while maintaining order| I[Group ID for Parallel Processing]
    I -->|Messages with same Group ID processed in order| J[Ordered Processing within Group]

    A --> K[Visual Illustration]
    K -->|Representation of message flow and processing| L[Message Flow Diagram]

    E --> M[Message Grouping in FIFO]
    M -->|Grouping messages into different Message Groups| N[Different Groups for Parallel Processing]
    N -->|Messages from different groups processed concurrently| O[Improved Throughput]

    A --> P[Direction of Travel and Consumption]
    P -->|Shows flow of messages and consumption order| Q[Directional Indicators]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,E,K,P subheading;
    class C,D,F,G,H,I,J,L,M,N,O,Q details;
```

## Comparison: Kinesis Data Streams vs SQS FIFO
```mermaid
graph LR
A[Comparison: Kinesis Data Streams vs SQS FIFO] --> B[Kinesis Data Streams]
B --> C[5 Shards]
C --> D[20 Trucks' Data per Shard]
C --> E[5 MB/s Incoming Data per Shard]
C --> F[5 Consumers per Shard]
F --> G[Data Ordered Within Each Shard]

    A --> H[SQS FIFO]
    H --> I[1 Queue with 100 Group IDs]
    I --> J[100 Consumers with Unique Group IDs]
    I --> K[300 Messages per Second, 3000 with Batching]
    J --> L[Order Maintained Within Each Group]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,H subheading;
    class C,D,E,F,G,I,J,K,L details;
```

## Amazon SQS, SNS, and Kinesis Comparison
```mermaid
graph LR
    A[Amazon SQS, SNS, and Kinesis Comparison] --> B[SQS]
    B --> C[Consumer Pull Data]
    B --> D[Data Deleted After Consumption]
    B --> E[Unlimited Consumers]
    B --> F[No Provisioning of Throughput]
    B --> G[Ordering in FIFO Queues]
    B --> H[Individual Message Delay]

    A --> I[SNS]
    I --> J[Push Data to Subscribers]
    I --> K[Up to 12,500,000 Subscribers]
    I --> L[Data Not Persisted]
    I --> M[Pub/Sub Model]
    I --> N[Up to 100,000 Topics]
    I --> O[No Provisioning of Throughput]
    I --> P[Integration with SQS for Fan-Out]
    I --> Q[FIFO for SQS FIFO]

    A --> R[Kinesis]
    R --> S[Standard: Pull Data, 2 MB per Shard]
    R --> T[Enhanced-Fan Out: Push Data, 2 MB per Shard/Consumer]
    R --> U[Data Replay Capability]
    R --> V[Real-Time Big Data, Analytics, ETL]
    R --> W[Ordering at Shard Level]
    R --> X[Data Expiry After Set Days]
    R --> Y[Provisioned or On-Demand Capacity]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,I,R subheading;
    class C,D,E,F,G,H,J,K,L,M,N,O,P,Q,S,T,U,V,W,X,Y details;
```


| Feature / Service | Amazon SQS                                      | Amazon SNS                                           | Amazon Kinesis                                      |
|-------------------|-------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------|
| Delivery Mechanism| Consumer "pull data"                            | Push data to many subscribers                        | Standard: Pull data (2 MB/shard), Enhanced: Push data (2 MB/shard/consumer) |
| Data Handling     | Data is deleted after being consumed            | Data is not persisted (lost if not delivered)        | Possibility to replay data                          |
| Consumers         | Can have as many workers (consumers) as wanted  | Up to 12,500,000 subscribers                         | Depends on shard configuration                       |
| Throughput        | No need to provision throughput                 | No need to provision throughput                      | Provisioned mode or on-demand capacity mode          |
| Ordering          | Ordering guarantees only on FIFO queues         | FIFO capability for SQS FIFO                         | Ordering at the shard level                          |
| Additional Features| Individual message delay capability            | Integrates with SQS for fan-out architecture pattern | Meant for real-time big data, analytics, and ETL     |
| Topics/Queues     | N/A                                             | Up to 100,000 topics                                 | N/A                                                  |
| Data Expiry       | N/A                                             | N/A                                                  | Data expires after X days                            |


## For exam

1. A geological research agency maintains the seismological data for the last 100 years. The data has a velocity of 1GB per minute. You would like to store the data with only the most relevant attributes to build a predictive model for earthquakes.

What AWS services would you use to build the most cost-effective solution with the LEAST amount of infrastructure maintenance?

***Answer:*** Ingest the data in Amazon Kinesis Data Firehose and use an intermediary AWS Lambda function to filter and transform the incoming stream before the output is dumped on Amazon S3

Amazon Kinesis Data Firehose is the easiest way to load streaming data into data stores and analytics tools. It can capture, transform, and load streaming data into Amazon S3, Amazon Redshift, Amazon OpenSearch Service, and Splunk, enabling near real-time analytics with existing business intelligence tools and dashboards you’re already using today. It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration. It can also batch, compress, and encrypt the data before loading it, minimizing the amount of storage used at the destination and increasing security.

```mermaid
graph LR
    A[Seismological Data Storage Solution] --> B[Data Ingestion with Amazon Kinesis Data Firehose]
    A --> C[Data Transformation with AWS Lambda]
    A --> D[Data Storage on Amazon S3]

    B --> E[Capture and Load Streaming Data]
    B --> F[Automatic Scaling and Fully Managed Service]

    C --> G[Filter and Transform Data]
    C --> H[Intermediary Function for Stream Processing]

    D --> I[Store Transformed Data]
    D --> J[Cost-effective and Secure Storage]

    A --> K[Minimal Infrastructure Maintenance]
    K --> L[Automated Scaling and Administration]
    K --> M[Batching, Compression, and Encryption of Data]

```

2. A gaming company is developing a mobile game that streams score updates to a backend processor and then publishes results on a leaderboard. The company has hired you as an AWS Certified Solutions Architect Associate to design a solution that can handle major traffic spikes, process the mobile game updates in the order of receipt, and store the processed updates in a highly available database. The company wants to minimize the management overhead required to maintain the solution.

Which of the following will you recommend to meet these requirements?

***Answer:*** Push score updates to Amazon Kinesis Data Streams which uses an AWS Lambda function to process these updates and then store these processed updates in Amazon DynamoDB

To help ingest real-time data or streaming data at large scales, you can use Amazon Kinesis Data Streams (KDS). KDS can continuously capture gigabytes of data per second from hundreds of thousands of sources. The data collected is available in milliseconds, enabling real-time analytics. KDS provides ordering of records, as well as the ability to read and/or replay records in the same order to multiple Amazon Kinesis Applications.

AWS Lambda integrates natively with Kinesis Data Streams. The polling, checkpointing, and error handling complexities are abstracted when you use this native integration. The processed data can then be configured to be saved in Amazon DynamoDB.

```mermaid
graph LR
    A[Solution for Mobile Game Score Processing] --> B[Push Score Updates to Amazon Kinesis Data Streams]
    A --> C[Use AWS Lambda for Processing Updates]
    A --> D[Store Processed Updates in Amazon DynamoDB]

    B --> E[Handle Major Traffic Spikes]
    B --> F[Ensure Order of Receipt]
    B --> G[Real-time Data Ingestion]

    C --> H[Native Integration with Kinesis]
    C --> I[Automate Polling, Checkpointing, and Error Handling]

    D --> J[Highly Available Database]
    D --> K[Minimize Management Overhead]

    A --> L[Recommended by AWS Certified Solutions Architect]
    L --> M[Optimized for Real-time Analytics and Scalability]
    M --> N[Efficient, Scalable, and Managed Solution]

```