
##  Amazon SNS
```mermaid
graph LR
A[Event Producer] -->|Sends messages to| B[SNS Topic]
B -->|Distributes messages to| C[Subscribers]
C --> D[Amazon SQS]
C --> E[AWS Lambda]
C --> F[Kinesis Data Firehose]
C --> G[Email/SMS/Mobile Notifications]
C --> H[HTTP Endpoints]
B -->|Message Filtering| I[Filter Based on Criteria]
B -->|Scalability and Limits| J[12,500,000 subscriptions/topic]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef services fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef filtering fill:#ddf,stroke:#333,stroke-width:2px;
    
    class A default;
    class B default;
    class C,I services;
    class D,E,F,G,H services;
    class J filtering;
```


##  Publish Messages using Amazon SNS
```mermaid
graph LR
A[Publish Messages using Amazon SNS] --> B[Topic Publish using the SDK]
B --> C[Create a Topic]
B --> D[Create a Subscription]
B --> E[Publish to the Topic]

    A --> F[Direct Publish for Mobile Apps SDK]
    F --> G[Create a Platform Application]
    F --> H[Create a Platform Endpoint]
    F --> I[Publish to the Platform Endpoint]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef step fill:#e6e6e6,stroke:#333,stroke-width:2px;
    
    class B,F default;
    class C,D,E,G,H,I step;

```

##  Amazon SNS Security Features
```mermaid
graph LR
A[Amazon SNS Security Features] --> B[Encryption]
B --> C[In-flight Encryption using HTTPS API]
B --> D[At-rest Encryption using KMS keys]
B --> E[Client-side Encryption]

    A --> F[Access Controls]
    F --> G[IAM Policies for SNS API]

    A --> H[SNS Access Policies]
    H --> I[Cross-Account Access]
    H --> J[Integration with other AWS Services]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef encryption fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef access fill:#ddf,stroke:#333,stroke-width:2px;
    
    class B encryption;
    class F,H access;
```



##  Amazon SNS SQS Fanout
```mermaid
graph LR
    A[Buying Service] -->|Publishes message to| B[SNS Topic]
    B -->|Delivers to all subscribed SQS queues| C[SQS Queue - Fraud Service]
    B -->|Delivers to all subscribed SQS queues| D[SQS Queue - Shipping Service]
    C -->|Allows for data persistence, delayed processing, retries| E[Fraud Processing]
    D -->|Allows for data persistence, delayed processing, retries| F[Shipping Processing]
    B -->|Add more SQS subscribers over time| G[New SQS Subscribers]
    B -->|Cross-Region Delivery| H[Multiple AWS Regions]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef service fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef queue fill:#ddf,stroke:#333,stroke-width:2px;
    classDef process fill:#ff9,stroke:#333,stroke-width:2px;

    class A,B service;
    class C,D,G,H queue;
    class E,F process;

```
```mermaid
graph LR
A[Amazon S3 Bucket] -->|Event Notification| B[SNS Topic]
B -->|Subscribes to SNS Topic| C[SQS Queue 1]
B -->|Subscribes to SNS Topic| D[SQS Queue 2]
B -->|Subscribes to SNS Topic| E[SQS Queue 3]
B -->|Subscribes to SNS Topic| F[AWS Lambda Function]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef s3 fill:#f96,stroke:#333,stroke-width:2px;
    classDef sns fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef sqs fill:#ddf,stroke:#333,stroke-width:2px;
    classDef lambda fill:#ff9,stroke:#333,stroke-width:2px;
    
    class A s3;
    class B sns;
    class C,D,E sqs;
    class F lambda;

```
```mermaid
graph LR
A[Buying Service] -->|Sends data to| B[SNS Topic]
B -->|Publishes data to| C[Kinesis Data Firehose]
C -->|Loads data into| D[Amazon S3]
C -->|Can also send to| E[Any Supported KDF Destination]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef sns fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef kdf fill:#ddf,stroke:#333,stroke-width:2px;
    classDef s3 fill:#f96,stroke:#333,stroke-width:2px;
    
    class A default;
    class B sns;
    class C kdf;
    class D s3;
    class E default;
```

```mermaid
graph LR
A[Amazon SNS  FIFO Topic] -->|Ordering by Message Group ID| B[Ordered Message Delivery]
A -->|Deduplication using ID or Content| C[Deduplication Mechanism]
A -->|SQS FIFO as Subscribers| D[SQS FIFO Queues]
A -->|Limited Throughput| E[Throughput Restrictions]
F[Producer] -->|Sends ordered messages| A
A -->|Ensures order preservation| G[Subscribers SQS FIFO]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef feature fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef producer fill:#ddf,stroke:#333,stroke-width:2px;
    
    class A default;
    class B,C,D,E feature;
    class F producer;
    class G default;
```

```mermaid
graph LR
A[Buying Service] -->|Publishes messages to| B[SNS FIFO Topic]
B -->|Distributes messages to| C[SQS FIFO Queue - Fraud Service]
B -->|Distributes messages to| D[SQS FIFO Queue - Shipping Service]
C -->|Processes messages| E[Fraud Service]
D -->|Processes messages| F[Shipping Service]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef sns fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef sqs fill:#ddf,stroke:#333,stroke-width:2px;
    classDef service fill:#ff9,stroke:#333,stroke-width:2px;
    
    class A default;
    class B sns;
    class C,D sqs;
    class E,F service;
```

##  Amazon SNS Filtering
```mermaid
graph LR
A[Buying Service] -->|Publishes transaction messages| B[SNS Topic]
B -->|Filter: State Placed| C[SQS Queue - Placed Orders]
B -->|Filter: State Cancelled| D[SQS Queue - Cancelled Orders]
B -->|Filter: State Declined| E[SQS Queue - Declined Orders]
B -->|No Filter| F[SQS Queue - All Messages]
B -->|Filter: State Cancelled| G[Email Subscription - Cancelled Orders]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef sns fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef sqs fill:#ddf,stroke:#333,stroke-width:2px;
    classDef email fill:#ff9,stroke:#333,stroke-width:2px;
    
    class A default;
    class B sns;
    class C,D,E,F sqs;
    class G email;
```


## For exam

1. The engineering team at a Spanish professional football club has built a notification system for its website using Amazon Simple Notification Service (Amazon SNS) notifications which are then handled by an AWS Lambda function for end-user delivery. During the off-season, the notification systems need to handle about 100 requests per second. During the peak football season, the rate touches about 5000 requests per second and it is noticed that a significant number of the notifications are not being delivered to the end-users on the website.

As a solutions architect, which of the following would you suggest as the BEST possible solution to this issue?


AWS Lambda currently supports 1000 concurrent executions per AWS account per region. If your Amazon SNS message deliveries to AWS Lambda contribute to crossing these concurrency quotas, your Amazon SNS message deliveries will be throttled. You need to contact AWS support to raise the account limit. Therefore this option is correct.



```mermaid
graph TD
    A[Issue: SNS Notifications Delivery at Peak Times] --> B[Scalability and Performance Optimization]
    B --> C[Evaluate and Increase AWS Lambda Concurrency Limits]

    C --> D[Check Concurrency Limits]
    C --> E[Request Increased Limits]

    D --> F[Default Limits per Region]
    E --> G[Through AWS Support Center]

    F --> H[Identify if Limits are Reached]
    G --> I[Increase as Needed for Demand]

    H --> J[Analyze Lambda Function Metrics]
    I --> K[Implement Changes and Monitor Performance]

    A --> L[Steps as Solutions Architect]
    L --> M[Step 1: Evaluate Lambda Concurrency Limits]
    M --> C

```