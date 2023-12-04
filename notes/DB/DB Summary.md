# DB Summary


## Types of Databases and Use Cases
```mermaid
graph LR
    Database_Types[Types of Databases and Use Cases] --> RDBMS[RDBMS]
    Database_Types --> NoSQL[NoSQL Databases]
    Database_Types --> Object_Store[Object Store]
    Database_Types --> Data_Warehouse[Data Warehouse]
    Database_Types --> Search[Search]
    Database_Types --> Graphs[Graphs]
    Database_Types --> Ledger[Ledger]
    Database_Types --> Time_Series[Time Series]

    RDBMS --> SQL_OLTP[SQL for OLTP]
    RDBMS --> Joins[Supports Joins]
    RDBMS --> Examples_RDBMS[RDS, Aurora]

    NoSQL --> DynamoDB[DynamoDB]
    NoSQL --> ElastiCache[ElastiCache]
    NoSQL --> Neptune[Neptune]
    NoSQL --> DocumentDB[DocumentDB]
    NoSQL --> Keyspaces[Keyspaces]

    Object_Store --> Amazon_S3[Amazon S3]
    Object_Store --> Glacier[Glacier]

    Data_Warehouse --> SQL_Analytics[SQL Analytics, BI]
    Data_Warehouse --> Examples_DWH[Redshift, Athena, EMR]

    Search --> OpenSearch[OpenSearch Elasticsearch]

Graphs --> Neptune_Graph[Amazon Neptune]

Ledger --> QLDB[Amazon Quantum Ledger Database]

Time_Series --> Timestream[Amazon Timestream]

style Database_Types fill:#f9f,stroke:#333,stroke-width:2px
style RDBMS fill:#cff,stroke:#333,stroke-width:2px
style NoSQL fill:#cff,stroke:#333,stroke-width:2px
style Object_Store fill:#cff,stroke:#333,stroke-width:2px
style Data_Warehouse fill:#cff,stroke:#333,stroke-width:2px
style Search fill:#cff,stroke:#333,stroke-width:2px
style Graphs fill:#cff,stroke:#333,stroke-width:2px
style Ledger fill:#cff,stroke:#333,stroke-width:2px
style Time_Series fill:#cff,stroke:#333,stroke-width:2px



```

## Amazon RDS Summary
```mermaid
graph LR
RDS[Amazon RDS Summary] --> Database_Engines[Supported Database Engines]
RDS --> Provisioning[Provisioning]
RDS --> Auto_Scaling[Auto-Scaling]
RDS --> High_Availability[High Availability]
RDS --> Security[Security]
RDS --> Backup[Backup]
RDS --> Maintenance[Maintenance]
RDS --> Integration[Integration]
RDS --> RDS_Custom[RDS Custom]
RDS --> Use_Case[Primary Use Case]

    Database_Engines --> Engines_List[PostgreSQL, MySQL, Oracle, SQL Server, MariaDB]
    Provisioning --> Instance_Size[Provision Instance Size]
    Provisioning --> EBS_Volume[EBS Volume Type and Size]
    Auto_Scaling --> Storage_Scaling[Storage Scaling]
    Auto_Scaling --> Read_Replicas[Read Replicas]
    High_Availability --> Multi_AZ[Multi-AZ Deployments]
    Security --> IAM_Security[IAM, Security Groups]
    Security --> KMS_SSL[KMS Encryption, SSL for Data Transit]
    Backup --> Automated_Backups[Automated Backups, Point-in-Time Restore]
    Backup --> DB_Snapshots[Manual DB Snapshots]
    Maintenance --> Managed_Maintenance[Managed and Scheduled Maintenance]
    Integration --> IAM_Auth[IAM Authentication]
    Integration --> Secrets_Manager[AWS Secrets Manager Integration]
    RDS_Custom --> Custom_Installation[Customize Oracle, SQL Server Instances]
    Use_Case --> OLTP_Systems[Relational Data, SQL Queries for OLTP]

    style RDS fill:#f9f,stroke:#333,stroke-width:2px
    style Database_Engines fill:#cff,stroke:#333,stroke-width:2px
    style Provisioning fill:#cff,stroke:#333,stroke-width:2px
    style Auto_Scaling fill:#cff,stroke:#333,stroke-width:2px
    style High_Availability fill:#cff,stroke:#333,stroke-width:2px
    style Security fill:#cff,stroke:#333,stroke-width:2px
    style Backup fill:#cff,stroke:#333,stroke-width:2px
    style Maintenance fill:#cff,stroke:#333,stroke-width:2px
    style Integration fill:#cff,stroke:#333,stroke-width:2px
    style RDS_Custom fill:#cff,stroke:#333,stroke-width:2px
    style Use_Case fill:#cff,stroke:#333,stroke-width:2px
```


## Amazon Aurora Summary
```mermaid
graph LR
Aurora_Summary[Amazon Aurora Summary] --> Compatibility[Compatibility]
Aurora_Summary --> Storage[Storage]
Aurora_Summary --> Clustering[Clustering]
Aurora_Summary --> Endpoints[Custom Endpoints]
Aurora_Summary --> Security_Monitoring[Security & Monitoring]
Aurora_Summary --> Backup_Restore[Backup & Restore]
Aurora_Summary --> Serverless[Serverless Options]
Aurora_Summary --> Multi_Master[Multi-Master]
Aurora_Summary --> Global_Databases[Global Databases]
Aurora_Summary --> ML_Integration[Machine Learning Integration]
Aurora_Summary --> Database_Cloning[Database Cloning]
Aurora_Summary --> Use_Case[Primary Use Case]

    Compatibility --> PostgreSQL_MySQL[PostgreSQL & MySQL]
    Storage --> Six_Replicas[Six Replicas Across Three AZs]
    Clustering --> Auto_Scaling[Auto-Scaling for Read Replicas]
    Endpoints --> Writer_Reader_Management[Manage Writer & Reader Instances]
    Security_Monitoring --> RDS_Par[Comparable to RDS]
    Backup_Restore --> Aurora_Specific[Specific Options for Aurora]
    Serverless --> Workloads[Unpredictable or Intermittent Workloads]
    Multi_Master --> Write_Failover[Continuous Write Failover]
    Global_Databases --> Read_Replicas[Up to 16 Read Replicas]
    Global_Databases --> Storage_Replication[Sub-Second Replication Times]
    ML_Integration --> SageMaker_Comprehend[Integrates with SageMaker & Comprehend]
    Database_Cloning --> Efficient_Cloning[Quick Cloning from Existing Cluster]
    Use_Case --> Enhanced_RDS[Similar to RDS but with Added Features]

    style Aurora_Summary fill:#f9f,stroke:#333,stroke-width:2px
    style Compatibility fill:#cff,stroke:#333,stroke-width:2px
    style Storage fill:#cff,stroke:#333,stroke-width:2px
    style Clustering fill:#cff,stroke:#333,stroke-width:2px
    style Endpoints fill:#cff,stroke:#333,stroke-width:2px
    style Security_Monitoring fill:#cff,stroke:#333,stroke-width:2px
    style Backup_Restore fill:#cff,stroke:#333,stroke-width:2px
    style Serverless fill:#cff,stroke:#333,stroke-width:2px
    style Multi_Master fill:#cff,stroke:#333,stroke-width:2px
    style Global_Databases fill:#cff,stroke:#333,stroke-width:2px
    style ML_Integration fill:#cff,stroke:#333,stroke-width:2px
    style Database_Cloning fill:#cff,stroke:#333,stroke-width:2px
    style Use_Case fill:#cff,stroke:#333,stroke-width:2px
```

## Amazon DynamoDB Summary
```mermaid
graph LR
DynamoDB_Summary[Amazon DynamoDB Summary] --> Managed_Serverless[Managed Serverless NoSQL Database]
DynamoDB_Summary --> Millisecond_Latency[Millisecond Latency]
DynamoDB_Summary --> Capacity_Modes[Capacity Modes]
DynamoDB_Summary --> TTL[Time to Live TTL Features]
DynamoDB_Summary --> High_Availability[High Availability]
DynamoDB_Summary --> DAX[DynamoDB Accelerator DAX]
DynamoDB_Summary --> Security[Security Features]
DynamoDB_Summary --> Streams[DynamoDB Streams]
DynamoDB_Summary --> Global_Table[Global Table]
DynamoDB_Summary --> Backups[Automated and On-Demand Backups]
DynamoDB_Summary --> Data_Export_Import[Data Export/Import to/from S3]
DynamoDB_Summary --> Schema_Evolution[Schema Evolution Support]

    Capacity_Modes --> Provisioned[Provisioned Capacity]
    Capacity_Modes --> On_Demand[On-Demand Capacity]

    High_Availability --> Multiple_AZs[Multiple Availability Zones]
    High_Availability --> Decoupled_Operations[Decoupled Read and Write Operations]

    Security --> IAM_Auth[Authentication & Authorization through IAM]

    Use_Case[Use Case] --> Serverless_Apps[Serverless Applications Development]
    Use_Case --> Small_Documents[Handling Small Documents]
    Use_Case --> Serverless_Caching[Distributed Serverless Caching]
    Use_Case --> Non_SQL[Optimized for Non-SQL Query Language]

    style DynamoDB_Summary fill:#f9f,stroke:#333,stroke-width:2px
    style Managed_Serverless fill:#cff,stroke:#333,stroke-width:2px
    style Millisecond_Latency fill:#cff,stroke:#333,stroke-width:2px
    style Capacity_Modes fill:#cff,stroke:#333,stroke-width:2px
    style TTL fill:#cff,stroke:#333,stroke-width:2px
    style High_Availability fill:#cff,stroke:#333,stroke-width:2px
    style DAX fill:#cff,stroke:#333,stroke-width:2px
    style Security fill:#cff,stroke:#333,stroke-width:2px
    style Streams fill:#cff,stroke:#333,stroke-width:2px
    style Global_Table fill:#cff,stroke:#333,stroke-width:2px
    style Backups fill:#cff,stroke:#333,stroke-width:2px
    style Data_Export_Import fill:#cff,stroke:#333,stroke-width:2px
    style Schema_Evolution fill:#cff,stroke:#333,stroke-width:2px
    style Use_Case fill:#cff,stroke:#333,stroke-width:2px
    style Serverless_Apps fill:#cfc,stroke:#333,stroke-width:2px
    style Small_Documents fill:#cfc,stroke:#333,stroke-width:2px
    style Serverless_Caching fill:#cfc,stroke:#333,stroke-width:2px
    style Non_SQL fill:#cfc,stroke:#333,stroke-width:2px
```

## Amazon S3 Summary
```mermaid
graph LR
S3_Summary[Amazon S3 Summary] --> Key_Value_Store[Key/Value Store]
S3_Summary --> Serverless_Infinite_Scalability[Serverless & Infinite Scalability]
S3_Summary --> Storage_Tiers[Storage Tiers]
S3_Summary --> Key_Features[Key Features]
S3_Summary --> Security[Security]
S3_Summary --> Encryption_Options[Encryption Options]
S3_Summary --> Operations[Operations]
S3_Summary --> Automation[Automation]
S3_Summary --> Use_Cases[Use Cases]

    Key_Value_Store --> Optimized_for_Larger_Objects[Optimized for Larger Objects]
    Serverless_Infinite_Scalability --> Object_Size[Max Object Size: 5 TB]
    Serverless_Infinite_Scalability --> Versioning[Versioning Capabilities]

    Storage_Tiers --> Standard[S3 Standard]
    Storage_Tiers --> Infrequent_Access[S3 Infrequent Access]
    Storage_Tiers --> Intelligent_Tiering[S3 Intelligent-Tiering]
    Storage_Tiers --> Glacier[S3 Glacier]

    Key_Features --> Versioning_Feature[Versioning]
    Key_Features --> Encryption_Feature[Encryption]
    Key_Features --> Replication[Replication]
    Key_Features --> MFA_Delete[MFA Delete]

    Security --> IAM_Security[IAM]
    Security --> Bucket_Policies[Bucket Policies]
    Security --> ACLs[ACLs]
    Security --> Access_Points[Access Points]

    Encryption_Options --> SSE_S3[SSE-S3]
    Encryption_Options --> SSE_KMS[SSE-KMS]
    Encryption_Options --> SSE_C[SSE-C]
    Encryption_Options --> Client_Side_Encryption[Client-Side Encryption]

    Operations --> Batch_Operations[Batch Operations]
    Operations --> Multi_Part_Uploads[Multi-Part Uploads]
    Operations --> Transfer_Acceleration[Transfer Acceleration]
    Operations --> S3_Select[S3 Select]

    Automation --> Event_Notifications[S3 Event Notifications]
    Automation --> Integration_Options[Integration with SNS, SQS, Lambda]

    Use_Cases --> Static_Files[Storing Static Files]
    Use_Cases --> Large_File_Storage[Key-Value Store for Large Files]
    Use_Cases --> Website_Hosting[Website Hosting]

    style S3_Summary fill:#f9f,stroke:#333,stroke-width:2px
    style Key_Value_Store fill:#cff,stroke:#333,stroke-width:2px
    style Serverless_Infinite_Scalability fill:#cff,stroke:#333,stroke-width:2px
    style Storage_Tiers fill:#cff,stroke:#333,stroke-width:2px
    style Key_Features fill:#cff,stroke:#333,stroke-width:2px
    style Security fill:#cff,stroke:#333,stroke-width:2px
    style Encryption_Options fill:#cff,stroke:#333,stroke-width:2px
    style Operations fill:#cff,stroke:#333,stroke-width:2px
    style Automation fill:#cff,stroke:#333,stroke-width:2px
    style Use_Cases fill:#cff,stroke:#333,stroke-width:2px

```

## Amazon DocumentDB Overview
```mermaid
graph LR
DocDB_Overview[DocumentDB Overview] --> Fully_Managed[Fully Managed NoSQL Database]
DocDB_Overview --> MongoDB_Compatibility[MongoDB Compatibility]
DocDB_Overview --> Deployment_Concepts[Similar Deployment as Amazon Aurora]
DocDB_Overview --> High_Availability[High Availability]
DocDB_Overview --> Automatic_Storage[Automatic Storage Scaling]
DocDB_Overview --> Scaling_Performance[Scaling for High Throughput & Low-Latency]

    Fully_Managed --> Managed_by_AWS[Fully Managed by AWS]
    MongoDB_Compatibility --> JSON_Data[Store, Query, Index JSON Data]
    Deployment_Concepts --> Aurora_Comparable[Comparable to Aurora]
    High_Availability --> Data_Replication[Data Replication Across 3 AZs]
    Automatic_Storage --> Scale_to_64TB[Scales up to 64TB]
    Scaling_Performance --> Millions_of_Requests[Handles Millions of Requests per Second]

    Benefits[Benefits] --> Scalable_Secure[Scalable and Secure]
    Benefits --> Optimized_JSON[Optimized for JSON Documents]
    Benefits --> AWS_Integration[Integration with AWS Services]
    Benefits --> AWS_Reliability[Reliability of AWS Managed Services]

    style DocDB_Overview fill:#f9f,stroke:#333,stroke-width:2px
    style Fully_Managed fill:#cff,stroke:#333,stroke-width:2px
    style MongoDB_Compatibility fill:#cff,stroke:#333,stroke-width:2px
    style Deployment_Concepts fill:#cff,stroke:#333,stroke-width:2px
    style High_Availability fill:#cff,stroke:#333,stroke-width:2px
    style Automatic_Storage fill:#cff,stroke:#333,stroke-width:2px
    style Scaling_Performance fill:#cff,stroke:#333,stroke-width:2px
    style Benefits fill:#cff,stroke:#333,stroke-width:2px
```

## Amazon Neptune Overview
```mermaid
graph LR
Neptune_Overview[Amazon Neptune Overview] --> Managed_Graph_DB[Fully Managed Graph Database]
Neptune_Overview --> Ideal_for_Connected_Datasets[Ideal for Highly Connected Datasets]
Neptune_Overview --> High_Availability[High Availability]
Neptune_Overview --> Read_Replicas[Supports up to 15 Read Replicas]
Neptune_Overview --> Optimized_for_Relationships[Optimized for Billions of Relationships]
Neptune_Overview --> Low_Latency_Queries[Millisecond Latency for Graph Queries]
Neptune_Overview --> Reliability[Highly Reliable Across AZs]
Neptune_Overview --> Use_Cases[Use Cases]

    Ideal_for_Connected_Datasets --> Example_Social_Network[Social Network Graphs]
    High_Availability --> Distributed_AZs[Distributed across 3 AZs]
    
    Use_Cases --> Knowledge_Graphs[Knowledge Graphs]
    Use_Cases --> Fraud_Detection[Fraud Detection]
    Use_Cases --> Recommendation_Engines[Recommendation Engines]
    Use_Cases --> Social_Networking[Social Networking]

    style Neptune_Overview fill:#f9f,stroke:#333,stroke-width:2px
    style Managed_Graph_DB fill:#cff,stroke:#333,stroke-width:2px
    style Ideal_for_Connected_Datasets fill:#cff,stroke:#333,stroke-width:2px
    style High_Availability fill:#cff,stroke:#333,stroke-width:2px
    style Read_Replicas fill:#cff,stroke:#333,stroke-width:2px
    style Optimized_for_Relationships fill:#cff,stroke:#333,stroke-width:2px
    style Low_Latency_Queries fill:#cff,stroke:#333,stroke-width:2px
    style Reliability fill:#cff,stroke:#333,stroke-width:2px
    style Use_Cases fill:#cff,stroke:#333,stroke-width:2px
    style Knowledge_Graphs fill:#cfc,stroke:#333,stroke-width:2px
    style Fraud_Detection fill:#cfc,stroke:#333,stroke-width:2px
    style Recommendation_Engines fill:#cfc,stroke:#333,stroke-width:2px
    style Social_Networking fill:#cfc,stroke:#333,stroke-width:2px
```

## Amazon Keyspaces
```mermaid
graph LR
Keyspaces_Summary[Amazon Keyspaces for Apache Cassandra Summary] --> Managed_Service[Managed Cassandra-Compatible Database]
Keyspaces_Summary --> Serverless_Scalable[Serverless, Scalable, Fully Managed by AWS]
Keyspaces_Summary --> Auto_Scaling[Automatic Scaling of Tables]
Keyspaces_Summary --> High_Availability[High Availability]
Keyspaces_Summary --> CQL[Uses Cassandra Query Language CQL]
Keyspaces_Summary --> Latency[Single-Digit Millisecond Latency]
Keyspaces_Summary --> Capacity_Modes[Capacity Modes]
Keyspaces_Summary --> Security_Features[Security Features]
Keyspaces_Summary --> Use_Cases[Use Cases]

    High_Availability --> Replication_AZs[Data Replicated Across Multiple AZs]
    Capacity_Modes --> On_Demand[On-Demand Mode]
    Capacity_Modes --> Provisioned[Provisioned with Auto-Scaling]
    Security_Features --> Encryption[Encryption]
    Security_Features --> Backup[Backup]
    Security_Features --> PITR[Point-In-Time Recovery]

    Use_Cases --> IoT_Data[IoT Device Data Storage]
    Use_Cases --> Time_Series[Time-Series Data Handling]
    Use_Cases --> NoSQL_Applications[Flexible NoSQL Applications]

    style Keyspaces_Summary fill:#f9f,stroke:#333,stroke-width:2px
    style Managed_Service fill:#cff,stroke:#333,stroke-width:2px
    style Serverless_Scalable fill:#cff,stroke:#333,stroke-width:2px
    style Auto_Scaling fill:#cff,stroke:#333,stroke-width:2px
    style High_Availability fill:#cff,stroke:#333,stroke-width:2px
    style CQL fill:#cff,stroke:#333,stroke-width:2px
    style Latency fill:#cff,stroke:#333,stroke-width:2px
    style Capacity_Modes fill:#cff,stroke:#333,stroke-width:2px
    style Security_Features fill:#cff,stroke:#333,stroke-width:2px
    style Use_Cases fill:#cff,stroke:#333,stroke-width:2px
```


## Amazon QLDB Summary
```mermaid
graph LR
QLDB_Summary[Amazon QLDB Summary] --> Ledger_Function[Functions as a Ledger for Financial Transactions]
QLDB_Summary --> Managed_Service[Fully Managed, Serverless, Highly Available]
QLDB_Summary --> Data_Replication[Data Replication Across 3 AZs]
QLDB_Summary --> Auditable_History[Auditable History of All Changes]
QLDB_Summary --> Immutability[Immutable and Cryptographically Verifiable]
QLDB_Summary --> Performance[High Performance]
QLDB_Summary --> Centralization[Centralized with Compliance]

    Managed_Service --> Serverless[Serverless Architecture]
    Performance --> Better_than_Blockchain[Better than Ledger Blockchain Frameworks]
    Centralization --> Financial_Regulation_Compliance[Compliance for Financial Regulations]

    Use_Cases[Use Cases] --> Regulated_Industries[Suitable for Regulated Industries]
    Use_Cases --> Audit_Trails[Applications Requiring Audit Trails]
    Use_Cases --> Industry_Applications[Finance, Supply Chain, Manufacturing, HR, Legal Operations]

    style QLDB_Summary fill:#f9f,stroke:#333,stroke-width:2px
    style Ledger_Function fill:#cff,stroke:#333,stroke-width:2px
    style Managed_Service fill:#cff,stroke:#333,stroke-width:2px
    style Data_Replication fill:#cff,stroke:#333,stroke-width:2px
    style Auditable_History fill:#cff,stroke:#333,stroke-width:2px
    style Immutability fill:#cff,stroke:#333,stroke-width:2px
    style Performance fill:#cff,stroke:#333,stroke-width:2px
    style Centralization fill:#cff,stroke:#333,stroke-width:2px
    style Use_Cases fill:#cff,stroke:#333,stroke-width:2px
    style Regulated_Industries fill:#cfc,stroke:#333,stroke-width:2px
    style Audit_Trails fill:#cfc,stroke:#333,stroke-width:2px
    style Industry_Applications fill:#cfc,stroke:#333,stroke-width:2px
```


## Amazon Timestream Summary
```mermaid
graph LR
Timestream_Summary[Amazon Timestream Summary] --> Managed_Database[Fully Managed, Fast, Scalable, Serverless]
Timestream_Summary --> Automatic_Scaling[Automatic Scaling]
Timestream_Summary --> High_Volume_Capability[Trillions of Events per Day]
Timestream_Summary --> Cost_Effectiveness[Faster & More Cost-Effective]
Timestream_Summary --> Query_Support[Scheduled Queries, Multi-Measure Records]
Timestream_Summary --> SQL_Compatibility[SQL Compatibility]
Timestream_Summary --> Data_Storage_Tiering[Data Storage Tiering]
Timestream_Summary --> Analytics_Functions[Built-In Time Series Analytics]
Timestream_Summary --> Data_Security[Data Security: Encryption]

    Automatic_Scaling --> Variable_Data_Rates[Adjusts for Variable Data Ingestion Rates]
    Data_Storage_Tiering --> Fast_Access_Recent[Fast Access for Recent Data]
    Data_Storage_Tiering --> Cost_Optimized_Historical[Cost-Optimized for Historical Data]
    Data_Security --> Encryption_Transit_AtRest[Encryption in Transit and at Rest]

    Use_Cases[Use Cases] --> IoT_Applications[IoT Applications]
    Use_Cases --> Operational_Applications[Operational Applications]
    Use_Cases --> Real_Time_Analytics[Real-Time Analytics]

    style Timestream_Summary fill:#f9f,stroke:#333,stroke-width:2px
    style Managed_Database fill:#cff,stroke:#333,stroke-width:2px
    style Automatic_Scaling fill:#cff,stroke:#333,stroke-width:2px
    style High_Volume_Capability fill:#cff,stroke:#333,stroke-width:2px
    style Cost_Effectiveness fill:#cff,stroke:#333,stroke-width:2px
    style Query_Support fill:#cff,stroke:#333,stroke-width:2px
    style SQL_Compatibility fill:#cff,stroke:#333,stroke-width:2px
    style Data_Storage_Tiering fill:#cff,stroke:#333,stroke-width:2px
    style Analytics_Functions fill:#cff,stroke:#333,stroke-width:2px
    style Data_Security fill:#cff,stroke:#333,stroke-width:2px
    style Use_Cases fill:#cff,stroke:#333,stroke-width:2px
```
```mermaid
graph LR
Data_Sources[Data Sources] --> IoT[AWS IoT]
Data_Sources --> Kinesis_Streams[Kinesis Data Streams]
Data_Sources --> Monitoring_Tools[Monitoring Tools]

    Data_Processing[Data Processing] --> Lambda[AWS Lambda Functions]
    Data_Processing --> MSK[Amazon Managed Streaming for Apache Kafka MSK]
    Data_Processing --> Kinesis_Analytics[Kinesis Data Analytics for Apache Flink]

    Amazon_Timestream[Amazon Timestream] --> Data_Storage[Ingestion, Storage, and Querying]

    Visualization_Analysis[Visualization and Analysis] --> QuickSight[Amazon QuickSight]
    Visualization_Analysis --> Grafana[Grafana]
    Visualization_Analysis --> SageMaker[Amazon SageMaker]

    Connectivity[Connectivity] --> JDBC_Connection[JDBC Connection]

    Monitoring_Tools --> Prometheus[Prometheus]
    Monitoring_Tools --> Telegraf[Telegraf]

    style Data_Sources fill:#f9f,stroke:#333,stroke-width:2px
    style Data_Processing fill:#cff,stroke:#333,stroke-width:2px
    style Amazon_Timestream fill:#cff,stroke:#333,stroke-width:2px
    style Visualization_Analysis fill:#cff,stroke:#333,stroke-width:2px
    style Connectivity fill:#cff,stroke:#333,stroke-width:2px

```
