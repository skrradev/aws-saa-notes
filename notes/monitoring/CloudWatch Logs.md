## Amazon CloudWatch Logs

```mermaid
graph LR
CloudWatch_Logs[Amazon CloudWatch Logs] --> Log_Groups[Log Groups]
CloudWatch_Logs --> Log_Streams[Log Stream]
CloudWatch_Logs --> Log_Expiration_Policies[Log Expiration Policies]
CloudWatch_Logs --> Export_Options[CloudWatch Logs Export Options]

    Log_Groups --> Group_Settings[Shared Settings: Retention, Monitoring, Access]
    Log_Streams --> Event_Sequences[Sequences of Log Events]
    Log_Expiration_Policies --> Retention_Deletion[Policies for Retention and Deletion]
    Export_Options --> S3[Amazon S3]
    Export_Options --> Kinesis_Data_Streams[Kinesis Data Streams]
    Export_Options --> Kinesis_Data_Firehose[Kinesis Data Firehose]
    Export_Options --> Lambda[AWS Lambda]
    Export_Options --> Elasticsearch[Elasticsearch]

    style CloudWatch_Logs fill:#f9f,stroke:#333,stroke-width:2px
```

## Amazon CloudWatch Sources

```mermaid
graph LR
CloudWatch_Logs[Amazon CloudWatch Logs] --> SDK[SDK]
CloudWatch_Logs --> Logs_Agent[CloudWatch Logs Agent]
CloudWatch_Logs --> Unified_Agent[CloudWatch Unified Agent]
CloudWatch_Logs --> Elastic_Beanstalk[Elastic Beanstalk]
CloudWatch_Logs --> ECS[Amazon ECS]
CloudWatch_Logs --> Lambda[AWS Lambda]
CloudWatch_Logs --> VPC_Flow_Logs[VPC Flow Logs]
CloudWatch_Logs --> API_Gateway[API Gateway]
CloudWatch_Logs --> CloudTrail[AWS CloudTrail]
CloudWatch_Logs --> Route_53[Route 53]

    SDK --> Programmatic_Logs[Programmatic Log Sending]
    Logs_Agent --> EC2_On_Premises[Logs from EC2/On-Premises]
    Unified_Agent --> More_Data_Types[Collects More Data Types]
    Elastic_Beanstalk --> Web_App_Logs[Web Application Logs]
    ECS --> Container_Logs[Containerized Application Logs]
    Lambda --> Function_Execution_Logs[Function Execution Logs]
    VPC_Flow_Logs --> IP_Traffic_Logs[IP Traffic Logs]
    API_Gateway --> API_Call_Logs[API Call Logs]
    CloudTrail --> Action_Logs[User/Role/AWS Service Action Logs]
    Route_53 --> DNS_Query_Logs[DNS Query Logs]

    style CloudWatch_Logs fill:#f9f,stroke:#333,stroke-width:2px

```


```mermaid
graph LR
CloudWatch_Features[CloudWatch Logs Features] --> Metric_Filters[Metric Filters]
CloudWatch_Features --> Logs_Insights[CloudWatch Logs Insights]

    Metric_Filters --> Transform_Log_Data[Transform Log Data into Metrics]
    Metric_Filters --> Example_Uses[Example Uses]
    Example_Uses --> Count_Errors[Count ERROR Entries]
    Example_Uses --> Track_IPs[Track Specific IP Addresses]

    Logs_Insights --> Interactive_Analysis[Interactive Analysis of Log Data]
    Logs_Insights --> Perform_Queries[Perform Queries and Visualize Data]
    Logs_Insights --> Correlate_Log_Groups[Correlate Across Log Groups]
    Logs_Insights --> Integration_Dashboards[Integration with Dashboards]

    style CloudWatch_Features fill:#f9f,stroke:#333,stroke-width:2px
```


## Amazon CloudWatch S3 Export

```mermaid
graph LR
S3_Export[S3 Export] --> Export_Purpose[Export Purpose]
S3_Export --> Log_Availability[Up to 12 Hours for Log Availability]
S3_Export --> CreateExportTask_API[CreateExportTask API Call]
S3_Export --> Data_Timeliness[Data Timeliness]

    Export_Purpose --> Archiving[Archiving Logs]
    Export_Purpose --> Analysis[Performing Complex Analysis]
    Export_Purpose --> Compliance[Compliance Reasons]

    Log_Availability --> Delay_Note[Delay up to 12 Hours for Availability]

    CreateExportTask_API --> Export_Job[Create a Job for Log Export to S3]

    Data_Timeliness --> Near_Real_Time[Near-Real-Time Requirement]
    Data_Timeliness --> Real_Time[Real-Time Requirement]
    Near_Real_Time --> Logs_Subscriptions[Use Logs Subscriptions]
    Real_Time --> Logs_Subscriptions

    style S3_Export fill:#f9f,stroke:#333,stroke-width:2px
```
## Amazon CloudWatch Subscription Filter

```mermaid
graph LR
CW_Logs[CloudWatch Logs] --> Subscription_Filter[Subscription Filter]
Subscription_Filter --> Lambda_Function[Lambda Function]
Subscription_Filter --> Elasticsearch_Service[Amazon Elasticsearch Service]
Subscription_Filter --> Kinesis_Firehose[Kinesis Data Firehose]
Subscription_Filter --> S3[Amazon S3]
Subscription_Filter --> Kinesis_Streams[Kinesis Data Streams]
Subscription_Filter --> Other_Destinations[Other Destinations]

    Lambda_Function --> Real_Time_Processing[Real-Time Data Processing]
    Elasticsearch_Service --> Real_Time_Analysis[Real-Time Data Analysis]
    Kinesis_Firehose --> Streaming_Delivery[Delivering Streaming Data]
    S3 --> Data_Storage[Log Data Storage]
    Kinesis_Streams --> Real_Time_Collection[Real-Time Data Collection]
    Other_Destinations --> Multiple_Services[Multiple AWS Services]

    style CW_Logs fill:#f9f,stroke:#333,stroke-width:2px
```


## Multi-Account & Multi-Region CloudWatch Logs

```mermaid
graph LR
CloudWatch_Logs[Multi-Account & Multi-Region CloudWatch Logs] --> AccountARegion1[Account A - Region 1]
CloudWatch_Logs --> AccountBRegion2[Account B - Region 2]
CloudWatch_Logs --> AccountBRegion3[Account B - Region 3]

    AccountARegion1 --> SubscriptionFilter1[Subscription Filter]
    AccountBRegion2 --> SubscriptionFilter2[Subscription Filter]
    AccountBRegion3 --> SubscriptionFilter3[Subscription Filter]

    SubscriptionFilter1 --> KinesisStreams[Kinesis Data Streams]
    SubscriptionFilter2 --> KinesisStreams
    SubscriptionFilter3 --> KinesisStreams

    KinesisStreams --> KinesisFirehose[Kinesis Data Firehose]
    KinesisFirehose --> S3[Amazon S3]

    style CloudWatch_Logs fill:#f9f,stroke:#333,stroke-width:2px
```

## CloudWatch Logs Agent on EC2

```mermaid

graph TD
No_Logs_By_Default[By default, no logs from EC2 to CloudWatch]
EC2_Instances[Amazon EC2 Instances] --> No_Logs_By_Default

    Install_Agent[Install CloudWatch Logs Agent on EC2] --> EC2_Instances

    IAM_Permissions[Ensure Correct IAM Permissions] --> Install_Agent

    Setup_On_Premises[CloudWatch Agent Can Be Setup On-Premises Too] --> IAM_Permissions

    Flow_To_CloudWatch[Log Data Flow to CloudWatch Logs] --> Setup_On_Premises

    style No_Logs_By_Default fill:#f96,stroke:#333,stroke-width:2px
    style Install_Agent fill:#f9f,stroke:#333,stroke-width:2px
    style IAM_Permissions fill:#ff9,stroke:#333,stroke-width:2px
    style Setup_On_Premises fill:#9f9,stroke:#333,stroke-width:2px
    style Flow_To_CloudWatch fill:#99f,stroke:#333,stroke-width:2px
```

## CloudWatch Logs Agent on EC2

```mermaid
graph TD
LogsAgent[CloudWatch Logs Agent] --> |Limited to sending log data| LogsFunction[Logs to CloudWatch Logs]

    UnifiedAgent[CloudWatch Unified Agent] --> |Collects system-level metrics| MetricsFunction[System Metrics RAM, Processes]
    UnifiedAgent --> |Collects logs| UnifiedLogsFunction[Logs to CloudWatch Logs]
    UnifiedAgent --> |Centralized configuration via SSM| ConfigFunction[SSM Parameter Store Configuration]

    style LogsAgent fill:#f96,stroke:#333,stroke-width:2px
    style UnifiedAgent fill:#9f9,stroke:#333,stroke-width:2px
    style LogsFunction fill:#ff9,stroke:#333,stroke-width:2px
    style MetricsFunction fill:#f9f,stroke:#333,stroke-width:2px
    style UnifiedLogsFunction fill:#99f,stroke:#333,stroke-width:2px
    style ConfigFunction fill:#f9f,stroke:#333,stroke-width:2px
```
## CloudWatch Unified Agent - Metrics

```mermaid
graph LR
A[CloudWatch Unified Agent - Metrics] --> B[Collected on Linux Server / EC2 Instance]
B --> C1[CPU Metrics]
C1 --> D1[active]
C1 --> D2[guest]
C1 --> D3[idle]
C1 --> D4[system]
C1 --> D5[user]
C1 --> D6[steal]
B --> C2[Disk Metrics]
C2 --> E1[free]
C2 --> E2[used]
C2 --> E3[total]
C2 --> E4[Disk IO]
B --> C3[RAM Metrics]
C3 --> F1[free]
C3 --> F2[inactive]
C3 --> F3[used]
C3 --> F4[total]
C3 --> F5[cached]
B --> C4[Netstat Metrics]
C4 --> G1[TCP and UDP connections]
C4 --> G2[net packets]
C4 --> G3[bytes]
B --> C5[Processes Metrics]
C5 --> H1[total]
C5 --> H2[dead]
C5 --> H3[blocked]
C5 --> H4[idle]
C5 --> H5[running]
C5 --> H6[sleep]
B --> C6[Swap Space Metrics]
C6 --> I1[free]
C6 --> I2[used]
C6 --> I3[used %]
B --> J[Reminder: EC2 instances have out-of-the-box metrics for disk, CPU, and network]
```



| Feature                 | CloudWatch Logs                          | Kibana                                  |
|-------------------------|------------------------------------------|-----------------------------------------|
| Primary Use             | Monitoring, storing, and accessing log data from AWS services | Visualization and management interface for Elasticsearch data |
| Real-time Monitoring    | Yes, with CloudWatch Logs Insights       | Yes, with real-time log streaming and analysis |
| Data Storage            | Logs are stored within CloudWatch Logs   | Depends on Elasticsearch cluster for storage |
| Visualization           | Basic graphs and metric filters          | Advanced visualizations with various chart types |
| Custom Dashboards       | Yes, with CloudWatch Dashboards          | Yes, with more customizable options     |
| Alerting                | Yes, with CloudWatch Alarms              | Yes, through Elasticsearch's alerting features |
| Log Data Aggregation    | Yes, can aggregate logs across accounts and regions | Yes, if Elasticsearch is configured to receive logs from various sources |
| Search Capabilities     | Basic search with filter patterns        | Advanced search with Elasticsearch query DSL |
| Scalability             | Managed by AWS, scales with usage        | Depends on the Elasticsearch cluster setup |
| Access Control          | Integrated with AWS IAM                  | Integrated with X-Pack security (part of the Elastic Stack) |
| Third-party Integrations| Limited compared to Kibana               | Extensive through Elasticsearch and Beats |
| Pricing                 | Pay for data ingestion, storage, and analysis | Free to use Kibana, cost associated with Elasticsearch usage |
| Setup and Maintenance   | Managed by AWS, minimal setup required   | Requires setup and maintenance of Elasticsearch cluster |


