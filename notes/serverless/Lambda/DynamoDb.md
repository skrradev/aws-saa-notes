
## Amazon DynamoDB

```mermaid
graph LR
DynamoDB[Amazon DynamoDB] -->|Type| NoSQL[NoSQL Database Service]
DynamoDB -->|Availability| High_Availability[High Availability & Durability]
DynamoDB -->|Workloads| Massive_Workloads[Handles Massive Workloads]
DynamoDB -->|Performance| Fast_Consistent_Performance[Fast & Consistent Performance]
DynamoDB -->|Security| Integrated_with_IAM[Integrated with IAM]
DynamoDB -->|Cost-Effectiveness| Cost_Effective[Cost-Effective]
DynamoDB -->|Management| No_Management_Tasks[Requires No Routine Management Tasks]
DynamoDB -->|Table_Classes| Table_Classes[Offers Table Classes]

    NoSQL --> KeyValue[Supports Key-Value & Document Structures]
    High_Availability --> Data_Replication[Replicates Data Across AZs]
    Massive_Workloads --> Auto_Scaling[Auto-Scaling for Throughput]
    Massive_Workloads --> High_Capacity[Supports Trillions of Rows & Large Storage]
    Fast_Consistent_Performance --> Millisecond_Response[Single-Digit Millisecond Response Times]
    Integrated_with_IAM --> Fine_Grained_Control[Fine-Grained Access Control]
    Cost_Effective --> Low_Cost_Operations[Low-Cost Read/Write Operations]
    Table_Classes --> Standard_Infrequent_Access[Standard & Infrequent Access Patterns]

    style DynamoDB fill:#f9f,stroke:#333,stroke-width:2px
    style NoSQL fill:#cff,stroke:#333,stroke-width:2px
    style High_Availability fill:#cff,stroke:#333,stroke-width:2px
    style Massive_Workloads fill:#cff,stroke:#333,stroke-width:2px
    style Fast_Consistent_Performance fill:#cff,stroke:#333,stroke-width:2px
    style Integrated_with_IAM fill:#cff,stroke:#333,stroke-width:2px
    style Cost_Effective fill:#cff,stroke:#333,stroke-width:2px
    style No_Management_Tasks fill:#cff,stroke:#333,stroke-width:2px
    style Table_Classes fill:#cff,stroke:#333,stroke-width:2px

```

## DynamoDB - Basics

```mermaid

graph LR
DynamoDB_Basics[DynamoDB - Basics] --> Tables[Tables]
DynamoDB_Basics --> Primary_Key[Primary Key]
DynamoDB_Basics --> Items[Items]
DynamoDB_Basics --> Attributes[Attributes]
DynamoDB_Basics --> Size_Limits[Size Limits]
DynamoDB_Basics --> Supported_Data_Types[Supported Data Types]
DynamoDB_Basics --> Schema_Flexibility[Schema Flexibility]

    Tables --> Table_Definition["Collection of Data Items"]
    Primary_Key --> Unique_Identifier["Unique Identifier for Items"]
    Items --> Item_Structure["Single Data Record, Variable Attributes"]
    Attributes --> Attribute_Characteristics["Data Elements, Can be Null"]
    Size_Limits --> Item_Size_Limit["Max 400KB per Item"]
    Supported_Data_Types --> Scalar_Types[Scalar Types]
    Supported_Data_Types --> Document_Types[Document Types]
    Supported_Data_Types --> Set_Types[Set Types]
    Schema_Flexibility --> Flexible_Schema_Design["Flexible Schema Design"]

    style DynamoDB_Basics fill:#f9f,stroke:#333,stroke-width:2px
    style Tables fill:#cff,stroke:#333,stroke-width:2px
    style Primary_Key fill:#cff,stroke:#333,stroke-width:2px
    style Items fill:#cff,stroke:#333,stroke-width:2px
    style Attributes fill:#cff,stroke:#333,stroke-width:2px
    style Size_Limits fill:#cff,stroke:#333,stroke-width:2px
    style Supported_Data_Types fill:#cff,stroke:#333,stroke-width:2px
    style Schema_Flexibility fill:#cff,stroke:#333,stroke-width:2px

```


## Capacity Modes in DynamoDB

```mermaid
graph LR
Capacity_Modes[Capacity Modes in DynamoDB] --> Provisioned_Mode[Provisioned Mode]
Capacity_Modes --> On_Demand_Mode[On-Demand Mode]

    Provisioned_Mode --> Capacity_Specification[Capacity Specification]
    Provisioned_Mode --> Capacity_Planning_Prov[Capacity Planning]
    Provisioned_Mode --> Cost_Prov[Cost]
    Provisioned_Mode --> Auto_Scaling[Auto-Scaling]

    On_Demand_Mode --> Scalability_OnDemand[Scalability]
    On_Demand_Mode --> Capacity_Planning_OnDemand[No Capacity Planning Needed]
    On_Demand_Mode --> Cost_OnDemand[Cost]
    On_Demand_Mode --> Suitability[Suitability]

    Capacity_Specification --> Specify_RCU_WCU["Specify RCUs and WCUs"]
    Capacity_Planning_Prov --> Upfront_Planning["Requires Upfront Planning"]
    Cost_Prov --> Pay_For_Provision["Pay for Provisioned RCUs/WCUs"]
    Auto_Scaling --> Auto_Adjust["Auto-adjust Throughput"]

    Scalability_OnDemand --> Auto_Scale_Up_Down["Automatically Scales Up/Down"]
    Capacity_Planning_OnDemand --> Fully_Managed["Fully Managed by DynamoDB"]
    Cost_OnDemand --> Pay_Per_Use["Pay for Actual Use"]
    Suitability --> Unpredictable_Workloads["Ideal for Unpredictable Workloads"]

    style Capacity_Modes fill:#f9f,stroke:#333,stroke-width:2px
    style Provisioned_Mode fill:#cff,stroke:#333,stroke-width:2px
    style On_Demand_Mode fill:#cff,stroke:#333,stroke-width:2px
    style Capacity_Specification fill:#cfc,stroke:#333,stroke-width:2px
    style Capacity_Planning_Prov fill:#cfc,stroke:#333,stroke-width:2px
    style Cost_Prov fill:#cfc,stroke:#333,stroke-width:2px
    style Auto_Scaling fill:#cfc,stroke:#333,stroke-width:2px
    style Scalability_OnDemand fill:#cfc,stroke:#333,stroke-width:2px
    style Capacity_Planning_OnDemand fill:#cfc,stroke:#333,stroke-width:2px
    style Cost_OnDemand fill:#cfc,stroke:#333,stroke-width:2px
    style Suitability fill:#cfc,stroke:#333,stroke-width:2px

```

## DynamoDB Accelerator (DAX)

```mermaid
graph LR
DAX[DynamoDB Accelerator DAX] --> Fully_Managed_Highly_Available[Fully Managed & Highly Available]
DAX --> In_Memory_Caching[In-Memory Caching]
DAX --> Latency[Low Latency]
DAX --> Solves_Read_Congestion[Solves Read Congestion]
DAX --> No_App_Logic_Modification[No Application Logic Modification]
DAX --> TTL[Time to Live TTL]
DAX --> Architecture[Architecture]

    Fully_Managed_Highly_Available --> No_Maintenance["Requires No Maintenance"]
    Fully_Managed_Highly_Available --> Multi_AZ["High Availability across AZs"]
    In_Memory_Caching --> Improved_Read_Performance["Improves Read Performance"]
    Latency --> Microsecond_Response_Times["Microsecond Response Times"]
    Solves_Read_Congestion --> Alleviate_Read_Congestion["Alleviates Read Congestion"]
    No_App_Logic_Modification --> Compatible_With_DynamoDB_API["Compatible with DynamoDB API"]
    TTL --> Default_TTL["Default TTL: 5 Minutes"]
    Architecture --> Between_Application_DynamoDB["Sits between Application and DynamoDB"]
    Architecture --> Multiple_Nodes["Comprises Multiple Nodes"]

    style DAX fill:#f9f,stroke:#333,stroke-width:2px
    style Fully_Managed_Highly_Available fill:#cff,stroke:#333,stroke-width:2px
    style In_Memory_Caching fill:#cff,stroke:#333,stroke-width:2px
    style Latency fill:#cff,stroke:#333,stroke-width:2px
    style Solves_Read_Congestion fill:#cff,stroke:#333,stroke-width:2px
    style No_App_Logic_Modification fill:#cff,stroke:#333,stroke-width:2px
    style TTL fill:#cff,stroke:#333,stroke-width:2px
    style Architecture fill:#cff,stroke:#333,stroke-width:2px

```

## In-Memory Caching Services

```mermaid
graph LR
Caching_Services[In-Memory Caching Services] --> ElastiCache[Amazon ElastiCache]
Caching_Services --> DAX[DynamoDB Accelerator DAX]

    ElastiCache --> Redis_Memcached_Backend[Redis or Memcached Back-end]
    ElastiCache --> General_Purpose_Caching[General Purpose Caching]
    ElastiCache --> Complex_Data_Types[Complex Data Types and Operations]
    ElastiCache --> Advanced_Data_Structures[Advanced Data Structures]
    ElastiCache --> Language_Agnostic[Language Agnostic]

    DAX --> DynamoDB_Backend[DynamoDB Back-end]
    DAX --> DynamoDB_Performance_Improvement[DynamoDB Performance Improvement]
    DAX --> Microsecond_Latency[Microsecond Latency]
    DAX --> API_Compatibility[API Compatibility]
    DAX --> Write_Through_Cache[Write-Through Cache]

    style Caching_Services fill:#f9f,stroke:#333,stroke-width:2px
    style ElastiCache fill:#cff,stroke:#333,stroke-width:2px
    style DAX fill:#cff,stroke:#333,stroke-width:2px
    style Redis_Memcached_Backend fill:#cfc,stroke:#333,stroke-width:2px
    style General_Purpose_Caching fill:#cfc,stroke:#333,stroke-width:2px
    style Complex_Data_Types fill:#cfc,stroke:#333,stroke-width:2px
    style Advanced_Data_Structures fill:#cfc,stroke:#333,stroke-width:2px
    style Language_Agnostic fill:#cfc,stroke:#333,stroke-width:2px
    style DynamoDB_Backend fill:#cfc,stroke:#333,stroke-width:2px
    style DynamoDB_Performance_Improvement fill:#cfc,stroke:#333,stroke-width:2px
    style Microsecond_Latency fill:#cfc,stroke:#333,stroke-width:2px
    style API_Compatibility fill:#cfc,stroke:#333,stroke-width:2px
    style Write_Through_Cache fill:#cfc,stroke:#333,stroke-width:2px
```


```mermaid
graph LR
DynamoDB_Streams[DynamoDB Streams] --> Processing_Layer[Processing Layer]

    Processing_Layer --> DynamoDB_KCL_Adapter[DynamoDB KCL Adapter]
    Processing_Layer --> AWS_Lambda[AWS Lambda]
    
    DynamoDB_Streams --> Integration_Services[Integration with AWS Services]
    Integration_Services --> Amazon_SNS[Amazon SNS]
    Integration_Services --> Amazon_Redshift[Amazon Redshift]
    Integration_Services --> Amazon_S3[Amazon S3]
    Integration_Services --> Amazon_Kinesis_Streams[Amazon Kinesis Data Streams]
    Integration_Services --> Kinesis_Data_Firehose[Kinesis Data Firehose]
    Integration_Services --> Amazon_OpenSearch_Service[Amazon OpenSearch Service]

    style DynamoDB_Streams fill:#f9f,stroke:#333,stroke-width:2px
    style Processing_Layer fill:#cff,stroke:#333,stroke-width:2px
    style DynamoDB_KCL_Adapter fill:#cfc,stroke:#333,stroke-width:2px
    style AWS_Lambda fill:#cfc,stroke:#333,stroke-width:2px
    style Integration_Services fill:#cff,stroke:#333,stroke-width:2px
    style Amazon_SNS fill:#cfc,stroke:#333,stroke-width:2px
    style Amazon_Redshift fill:#cfc,stroke:#333,stroke-width:2px
    style Amazon_S3 fill:#cfc,stroke:#333,stroke-width:2px
    style Amazon_Kinesis_Streams fill:#cfc,stroke:#333,stroke-width:2px
    style Kinesis_Data_Firehose fill:#cfc,stroke:#333,stroke-width:2px
    style Amazon_OpenSearch_Service fill:#cfc,stroke:#333,stroke-width:2px
```

## DynamoDB Global Tables

```mermaid
graph LR
Global_Tables[DynamoDB Global Tables] --> Low_Latency_Access[Low Latency Access]
Global_Tables --> Active_Active_Replication[Active-Active Replication]
Global_Tables --> Read_Write_Anywhere[Read and Write Anywhere]
Global_Tables --> DynamoDB_Streams_Prerequisite[DynamoDB Streams Prerequisite]

    subgraph Region_1
    Table_1_A[Table in Region e.g., US-EAST-1]
    end

    subgraph Region_2
    Table_2_B[Table in Region e.g., AP-SOUTHEAST-2]
    end

    Table_1_A <--> |Replication| Table_2_B
    Table_2_B <--> |Replication| Table_1_A

    style Global_Tables fill:#f9f,stroke:#333,stroke-width:2px
    style Low_Latency_Access fill:#cff,stroke:#333,stroke-width:2px
    style Active_Active_Replication fill:#cff,stroke:#333,stroke-width:2px
    style Read_Write_Anywhere fill:#cff,stroke:#333,stroke-width:2px
    style DynamoDB_Streams_Prerequisite fill:#cff,stroke:#333,stroke-width:2px
    style Table_1_A fill:#cfc,stroke:#333,stroke-width:2px
    style Table_2_B fill:#cfc,stroke:#333,stroke-width:2px

```


## DynamoDB TTL

```mermaid
graph LR
DynamoDB_TTL[DynamoDB TTL] --> Automatic_Deletion[Automatic Deletion]
DynamoDB_TTL --> Use_Cases[Use Cases]

    Automatic_Deletion --> Table[Table with TTL Column]
    Automatic_Deletion --> Current_Time[Current Time Indicator]
    Automatic_Deletion --> Expiry_Process[Expiration Process]

    Table --> User_ID_Column[User_ID]
    Table --> Session_ID_Column[Session_ID]
    Table --> ExpTime_Column[ExpTime TTL]

    Expiry_Process --> Scan_Process[Scan for Expiry]
    Expiry_Process --> Deletion[Deletion of Items]

    Use_Cases --> Removing_Outdated_Data[Removing Outdated Data]
    Use_Cases --> Regulatory_Compliance[Regulatory Compliance]
    Use_Cases --> Temporary_Data_Management[Managing Temporary Data]

    style DynamoDB_TTL fill:#f9f,stroke:#333,stroke-width:2px
    style Automatic_Deletion fill:#cff,stroke:#333,stroke-width:2px
    style Use_Cases fill:#cff,stroke:#333,stroke-width:2px
    style Table fill:#cfc,stroke:#333,stroke-width:2px
    style Current_Time fill:#cfc,stroke:#333,stroke-width:2px
    style Expiry_Process fill:#cfc,stroke:#333,stroke-width:2px
    style User_ID_Column fill:#cfc,stroke:#333,stroke-width:2px
    style Session_ID_Column fill:#cfc,stroke:#333,stroke-width:2px
    style ExpTime_Column fill:#cfc,stroke:#333,stroke-width:2px
    style Scan_Process fill:#cfc,stroke:#333,stroke-width:2px
    style Deletion fill:#cfc,stroke:#333,stroke-width:2px
    style Removing_Outdated_Data fill:#cfc,stroke:#333,stroke-width:2px
    style Regulatory_Compliance fill:#cfc,stroke:#333,stroke-width:2px
    style Temporary_Data_Management fill:#cfc,stroke:#333,stroke-width:2px
```

## DynamoDB Backup Options

```mermaid
graph LR
DynamoDB_Backup_Options[DynamoDB Backup Options] --> Continuous_Backups[Continuous Backups with PITR]
DynamoDB_Backup_Options --> On_Demand_Backups[On-Demand Backups]

    Continuous_Backups --> PITR_Feature[PITR Feature]
    Continuous_Backups --> Recovery_Process_PITR[Recovery Process]
    PITR_Feature --> Restore_To_Any_Point[Restore to Any Point in Last 35 Days]
    Recovery_Process_PITR --> New_Table_Creation_PITR[Creates New Table on Recovery]

    On_Demand_Backups --> Manual_Initiation[Manual Initiation]
    On_Demand_Backups --> Long_Term_Retention[Long-Term Retention]
    On_Demand_Backups --> Performance_Impact[No Impact on Performance]
    On_Demand_Backups --> AWS_Backup_Management[AWS Backup Management]
    AWS_Backup_Management --> Cross_Region_Copies[Cross-Region Backup Copies]
    On_Demand_Backups --> New_Table_Creation_OnDemand[Creates New Table on Recovery]

    style DynamoDB_Backup_Options fill:#f9f,stroke:#333,stroke-width:2px
    style Continuous_Backups fill:#cff,stroke:#333,stroke-width:2px
    style On_Demand_Backups fill:#cff,stroke:#333,stroke-width:2px
    style PITR_Feature fill:#cfc,stroke:#333,stroke-width:2px
    style Recovery_Process_PITR fill:#cfc,stroke:#333,stroke-width:2px
    style Restore_To_Any_Point fill:#cfc,stroke:#333,stroke-width:2px
    style New_Table_Creation_PITR fill:#cfc,stroke:#333,stroke-width:2px
    style Manual_Initiation fill:#cfc,stroke:#333,stroke-width:2px
    style Long_Term_Retention fill:#cfc,stroke:#333,stroke-width:2px
    style Performance_Impact fill:#cfc,stroke:#333,stroke-width:2px
    style AWS_Backup_Management fill:#cfc,stroke:#333,stroke-width:2px
    style Cross_Region_Copies fill:#cfc,stroke:#333,stroke-width:2px
    style New_Table_Creation_OnDemand fill:#cfc,stroke:#333,stroke-width:2px

```


## DynamoDB Integration with Amazon S3

```mermaid
graph LR
DynamoDB_S3_Integration[DynamoDB Integration with Amazon S3] --> Export_to_S3[Export to S3]
DynamoDB_S3_Integration --> Import_to_S3[Import to S3]

    Export_to_S3 --> PITR_Requirement[PITR Required]
    Export_to_S3 --> Export_Data_Analysis[Data Analysis on S3]
    Export_to_S3 --> Data_Retention[Auditing & Data Retention]
    Export_to_S3 --> ETL_Processing[ETL Processing]
    Export_to_S3 --> Export_Format[Data Export Format]

    Import_to_S3 --> Supported_File_Formats[Supported File Formats]
    Import_to_S3 --> No_Write_Capacity_Consumption[Does Not Consume Write Capacity]
    Import_to_S3 --> New_Table_Creation[Creates New Table]
    Import_to_S3 --> Error_Logging[Error Logging in CloudWatch]

    style DynamoDB_S3_Integration fill:#f9f,stroke:#333,stroke-width:2px
    style Export_to_S3 fill:#cff,stroke:#333,stroke-width:2px
    style Import_to_S3 fill:#cff,stroke:#333,stroke-width:2px
    style PITR_Requirement fill:#cfc,stroke:#333,stroke-width:2px
    style Export_Data_Analysis fill:#cfc,stroke:#333,stroke-width:2px
    style Data_Retention fill:#cfc,stroke:#333,stroke-width:2px
    style ETL_Processing fill:#cfc,stroke:#333,stroke-width:2px
    style Export_Format fill:#cfc,stroke:#333,stroke-width:2px
    style Supported_File_Formats fill:#cfc,stroke:#333,stroke-width:2px
    style No_Write_Capacity_Consumption fill:#cfc,stroke:#333,stroke-width:2px
    style New_Table_Creation fill:#cfc,stroke:#333,stroke-width:2px
    style Error_Logging fill:#cfc,stroke:#333,stroke-width:2px

```

