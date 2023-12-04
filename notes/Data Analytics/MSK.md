# Amazon MSK Kafka

```mermaid
graph LR
    Amazon_MSK[Amazon MSK] --> Fully_Managed[Fully Managed]
    Amazon_MSK --> Cluster_Operations[Cluster Operations]
    Amazon_MSK --> Broker_Zookeeper_Management[Broker and Zookeeper Management]
    Amazon_MSK --> Deployment_High_Availability[Deployment and High Availability]
    Amazon_MSK --> Automatic_Recovery[Automatic Recovery]
    Amazon_MSK --> Data_Storage[Data Storage]
    Amazon_MSK --> MSK_Serverless[MSK Serverless]

    Fully_Managed --> AWS_Manages_Clusters[AWS Manages Kafka Clusters]
    Cluster_Operations --> AWS_Console_CLI_SDK[AWS Management Console, CLI, SDKs]
    Broker_Zookeeper_Management --> Kafka_Broker_Zookeeper[Kafka Broker & Zookeeper Nodes]
    Deployment_High_Availability --> Amazon_VPC_Multi_Zone[Amazon VPC, Multi-Zone Availability]
    Automatic_Recovery --> Recover_Kafka_Failures[Recovers from Kafka Failures]
    Data_Storage --> Stored_on_EBS[Stored on Amazon EBS Volumes]
    MSK_Serverless --> No_Infrastructure_Management[No Infrastructure Management]

    Amazon_MSK --> Use_Case[Use Case]
    Use_Case --> Existing_Kafka_Users[Existing Kafka Users]
    Use_Case --> Event_Streaming_Apps[Event Streaming Applications]

    style Amazon_MSK fill:#f9f,stroke:#333,stroke-width:2px
    style Use_Case fill:#cff,stroke:#333,stroke-width:2px



```

```mermaid
graph LR
Apache_Kafka[Apache Kafka] --> Producers[Producers]
Apache_Kafka --> Brokers[Brokers]
Apache_Kafka --> Topics[Topics]
Apache_Kafka --> Replication[Replication]
Apache_Kafka --> Consumers[Consumers]
Apache_Kafka --> AWS_Integration[Integration with AWS Services]

    Producers --> Applications_Servers_Sensors[Applications, Servers, Sensors]
    Brokers --> Store_Serve_Data[Store Data and Serve Clients]
    Topics --> Multi_Subscriber[Multi-Subscriber Topics]
    Replication --> Data_Reliability[Ensure Data Reliability]
    Consumers --> Read_Ordered_Data[Read Data in Order]

    AWS_Integration --> Lambda[AWS Lambda]
    AWS_Integration --> S3[Amazon S3]
    AWS_Integration --> EMR[Amazon EMR]
    AWS_Integration --> SageMaker[Amazon SageMaker]

    style Apache_Kafka fill:#f9f,stroke:#333,stroke-width:2px

```

```mermaid
graph LR
Amazon_MSK[Amazon MSK] --> Kinesis_Data_Analytics[Kinesis Data Analytics for Apache Flink]
Amazon_MSK --> AWS_Glue_ETL[AWS Glue Streaming ETL Jobs]
Amazon_MSK --> Lambda[AWS Lambda]
Amazon_MSK --> EC2_Applications[Applications on Amazon EC2]
Amazon_MSK --> ECS_Applications[Applications on ECS]
Amazon_MSK --> EKS_Applications[Applications on EKS]

    Kinesis_Data_Analytics --> Process_Analyze_Streaming[Process & Analyze Streaming Data]
    AWS_Glue_ETL --> Real_Time_ETL[Real-Time ETL Operations]
    Lambda --> Event_Driven_Processing[Event-Driven Processing]
    EC2_Applications --> Virtual_Servers[Virtual Servers]
    ECS_Applications --> Docker_Containers[Docker Container Orchestration]
    EKS_Applications --> Kubernetes_Management[Managed Kubernetes Service]

    style Amazon_MSK fill:#f9f,stroke:#333,stroke-width:2px

```



| Feature                   | Kinesis Data Streams              | Amazon MSK                        |
|---------------------------|-----------------------------------|-----------------------------------|
| Message Size Limit        | 1 MB                              | 1 MB (configurable up to 10MB)    |
| Data Management           | Shards                            | Kafka Topics with Partitions      |
| Shard/Partition Changes   | Shard Splitting & Merging         | Can only add partitions to a topic|
| In-flight Encryption      | TLS                               | PLAINTEXT or TLS                  |
| At-rest Encryption        | KMS                               | KMS                               |
| Management                | AWS Managed                       | Fully managed Apache Kafka        |
| Integration               | AWS services integration          | Kafka ecosystem                   |


