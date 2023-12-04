# RDS

```mermaid
graph TD;
    RDS[("Amazon RDS\nManaged Relational Database Service\n-")]
    RDS -->|Automates| Administration[("Database Administration\n- Automated backups\n- Software patching\n-")]
    RDS -->|Scales| Resources[("Resource Scaling\n- Compute\n- Storage\n-")]
    RDS -->|Enhances| HA[("High Availability\n- Multi-AZ deployments\n-")]
    RDS -->|Ensures| DR[("Disaster Recovery\n- Read Replicas\n- Snapshots\n-")]
    RDS -->|Supports| Security[("Security Features\n- Encryption at rest and in transit\n- IAM\n- VPC\n-")]
    RDS -->|Enables| Monitoring[("Monitoring & Metrics\n- CloudWatch\n- Event notifications\n-")]
    RDS -->|Integrates| Services[("Service Integration\n- IAM\n- Lambda\n- Elastic Beanstalk\n-")]

    Administration -->|DB Operations| DBManagement[("DB Management Tasks\n- Automatic failover\n-")]
    Resources -->|Modification| ScalingUp[("Scaling Up/Down\n- With minimal downtime\n-")]
    HA -->|Data Durability| SynchronousReplication[("Synchronous Replication\n- For Multi-AZ\n-")]
    DR -->|Data Recovery| BackupRecovery[("Point-in-time Recovery\n-")]
    Security -->|Network Isolation| SubnetGroups[("DB Subnet Groups\n-")]
    Monitoring -->|Performance Insights| PerformanceMetrics[("Performance Insights\n- Database performance tuning\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class RDS,Administration,Resources,HA,DR,Security,Monitoring,Services important;


```


## RDS Storage Auto Scaling

```mermaid
graph TD;
StorageAutoScaling[("RDS Storage Auto Scaling")]
StorageAutoScaling -->|Automatically adjusts storage| AutoAdjust[("Automatic Adjustment\n- Based on the threshold")]
StorageAutoScaling -->|Monitors storage usage| MonitorUsage[("Monitoring Usage\n- Watches available storage space")]
StorageAutoScaling -->|Prevents downtime| PreventDowntime[("Prevent Downtime\n- No manual intervention needed")]
StorageAutoScaling -->|Cost management| ManageCost[("Cost Management\n- Pay for what you use")]
StorageAutoScaling -->|Configurable threshold| ConfigThreshold[("Configurable Threshold\n- Customize scaling trigger point")]
StorageAutoScaling -->|Supports most RDS instances| SupportRDS[("Support for RDS Instances\n- General Purpose (SSD), Provisioned IOPS")]

    AutoAdjust -->|Seamless experience| Seamless[("Seamless Scaling\n- No impact on DB performance")]
    MonitorUsage -->|CloudWatch metrics| CWIntegration[("CloudWatch Integration\n- Uses RDS metrics")]
    PreventDowntime -->|Automated operations| AutomatedOps[("Automated Operations\n- Scale without outages")]
    ManageCost -->|Scalable increments| Increments[("Increments\n- Scales in defined increments")]
    ConfigThreshold -->|User defined| UserDefined[("User-Defined Setting\n- Based on usage pattern")]
    SupportRDS -->|Excludes some types| Exclusions[("Exclusions\n- Not for all storage types")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class StorageAutoScaling,AutoAdjust,MonitorUsage,PreventDowntime,ManageCost,ConfigThreshold,SupportRDS important;
```



## RDS Read Replicas
```mermaid
graph TD;
ReadReplicas[("Amazon RDS Read Replicas")]
ReadReplicas -->|Improves Performance| Performance[("Performance Enhancement\n- Offload read traffic")]
ReadReplicas -->|Enhances Scalability| Scalability[("Scalability\n- Handle large numbers of read operations")]
ReadReplicas -->|Supports Cross-Region| CrossRegion[("Cross-Region Replication\n- Geographic distribution")]
ReadReplicas -->|Facilitates Reporting| Reporting[("Reporting & Analytics\n- Run queries without impacting primary")]
ReadReplicas -->|Disaster Recovery| DisasterRecovery[("Disaster Recovery\n- Promote to primary if needed")]
ReadReplicas -->|Data Backup| Backup[("Data Backup\n- Additional backup source")]

    Performance -->|Reduce Load| ReduceLoad[("Reduce Primary Load\n- Balance queries")]
    Scalability -->|Multiple Replicas| MultipleReplicas[("Multiple Replicas\n- Up to 5 replicas")]
    CrossRegion -->|Global Expansion| GlobalExpansion[("Global Expansion\n- Serve global users")]
    Reporting -->|Dedicated Replica| DedicatedReporting[("Dedicated Reporting Replica\n- Isolate reporting workload")]
    DisasterRecovery -->|Promotion| ReplicaPromotion[("Replica Promotion\n- Become standalone DB")]
    Backup -->|Point-in-time Restore| PITRestore[("Point-in-time Restore\n- From replica snapshots")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class ReadReplicas,Performance,Scalability,CrossRegion,Reporting,DisasterRecovery,Backup important;
```


## RDS Read Replicas Use Cases
```mermaid
graph TD;
UseCases[("Amazon RDS Read Replicas\nUse Cases")]
UseCases -->|Performance| LoadBalancing[("Read Load Balancing\n- Distribute read queries to improve performance")]
UseCases -->|Scalability| HandleReads[("Handle High Volume Reads\n- Scale out read capacity for high demand")]
UseCases -->|Data Locality| LocalReads[("Data Locality\n- Serve read requests closer to users geographically")]
UseCases -->|Reporting| ReportingDB[("Reporting & Analytics\n- Offload heavy analytics queries")]
UseCases -->|Backup| BackupLoad[("Reduce Backup Load\n- Perform backups on the replica to reduce primary load")]
UseCases -->|Disaster Recovery| Failover[("Disaster Recovery\n- Promote replica to primary for quick failover")]

    LoadBalancing -->|Multiple Replicas| MultipleEndpoints[("Multiple Endpoints\n- Spread connections across replicas")]
    HandleReads -->|Scale with Demand| DynamicScaling[("Dynamic Scaling\n- Add or remove replicas based on load")]
    LocalReads -->|Cross-Region Replicas| CrossRegion[("Cross-Region Replicas\n- Reduce read latency for global users")]
    ReportingDB -->|Dedicated Resources| DedicatedReplica[("Dedicated Replica\n- Isolate workload from operational database")]
    BackupLoad -->|Off-Peak Hours| OffPeakBackups[("Off-Peak Backups\n- Schedule backups during low traffic")]
    Failover -->|High Availability| Availability[("Increase Availability\n- Maintain service during primary outage")]

    classDef usecase fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class UseCases,LoadBalancing,HandleReads,LocalReads,ReportingDB,BackupLoad,Failover usecase;
```

## RDS Read Replicas Network Costs
```mermaid
graph TD;
NetworkCosts[("RDS Read Replicas Network Costs")]
NetworkCosts -->|Cross-region Replication| CrossRegionCost[("Cross-region Data Transfer Costs\n- Higher cost for data transfer between regions")]
NetworkCosts -->|In-region Replication| InRegionCost[("In-region Data Transfer Costs\n- Generally no cost within the same region")]
NetworkCosts -->|Internet Data Transfer| InternetCost[("Data Transfer to Internet\n- Costs for data transfer out to the internet")]
NetworkCosts -->|AZ Data Transfer| AZCost[("Availability Zone Data Transfer Costs\n- Costs for data transfer between AZs in the same region")]

    CrossRegionCost -->|Use Case| GlobalUsers[("For Global User Base\n- Consider replication needs vs cost")]
    InRegionCost -->|Use Case| RegionalUsers[("For Regional User Base\n- Typically lower or no costs involved")]
    InternetCost -->|Consideration| PublicAccess[("Publicly Accessible Data\n- Consider using CloudFront to reduce costs")]
    AZCost -->|Consideration| MultiAZDeployment[("Multi-AZ Deployments\n- Additional cost for high availability")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class NetworkCosts,CrossRegionCost,InRegionCost,InternetCost,AZCost important;
    
```

## RDS Multi-AZ Deployments
```mermaid
graph TD;
MultiAZ[("RDS Multi-AZ Deployments")]
MultiAZ -->|Purpose| HA[("High Availability")]
MultiAZ -->|Data Protection| SyncReplication[("Synchronous Replication")]
MultiAZ -->|Failover Process| AutomaticFailover[("Automatic Failover")]
MultiAZ -->|Read Operations| StandbyReads[("Standby Cannot be Read")]
MultiAZ -->|Backup| BackupRetention[("Enhanced Backup Retention")]
MultiAZ -->|Maintenance| MaintenanceWindows[("Maintenance Windows\n- No downtime")]

    HA -->|Downtime Reduction| DowntimeReduction[("Minimal Downtime\n- During outages\n-")]
    SyncReplication -->|Data Consistency| DataConsistency[("Data Consistency\n- Across AZs\n-")]
    AutomaticFailover -->|Primary Outage| PrimaryOutageHandling[("Handles Primary Outage\n- Transparent to application\n-")]
    StandbyReads -->|Latency Reduction| LatencyReduction[("Reduces Latency\n- During failover\n-")]
    BackupRetention -->|Point-in-time Restore| PITRestore[("Point-in-time Restore\n- From any backup\n-")]
    MaintenanceWindows -->|Zero Downtime| ZeroDowntime[("Zero Downtime\n- During DB updates\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class MultiAZ,HA,SyncReplication,AutomaticFailover,StandbyReads,BackupRetention,MaintenanceWindows important;
```

## RDS DB Standby Instance
```mermaid
graph TD;
    StandbyInstance[("RDS DB Standby Instance")]
    StandbyInstance -->|Purpose| HA[("High Availability\n- For fault tolerance\n-")]
    StandbyInstance -->|Synchronization| DataSync[("Synchronous Data Replication\n- To ensure data consistency\n-")]
    StandbyInstance -->|Failover| AutoFailover[("Automatic Failover\n- In case of primary instance failure\n-")]
    StandbyInstance -->|Accessibility| NoDirectAccess[("No Direct Access\n- Standby cannot be used for read or write\n-")]
    StandbyInstance -->|Backup| BackupFromStandby[("Backup\n- Taken from the standby to reduce primary load\n-")]
    StandbyInstance -->|Location| DifferentAZ[("Different Availability Zone\n- For disaster recovery\n-")]

    HA -->|Minimizes Downtime| MinDowntime[("Minimize Downtime\n- During planned maintenance\n-")]
    DataSync -->|Zero Data Loss| ZeroDataLoss[("Zero Data Loss Goal\n- On instance failure\n-")]
    AutoFailover -->|Seamless Transition| Seamless[("Seamless Transition\n- To standby without intervention\n-")]
    NoDirectAccess -->|Traffic Redirect| TrafficRedirect[("Traffic Redirect\n- Automatically on failover\n-")]
    BackupFromStandby -->|Performance| MaintainPerformance[("Maintain Performance\n- Of the primary during backups\n-")]
    DifferentAZ -->|Geographical Redundancy| GeoRedundancy[("Geographical Redundancy\n- Protects against zone failures\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class StandbyInstance,HA,DataSync,AutoFailover,NoDirectAccess,BackupFromStandby,DifferentAZ important;

```


## Amazon RDS Custom
```mermaid
graph TD;
RDSCustom[("Amazon RDS Custom")]
RDSCustom -->|Flexibility| Customization[("Customization\n- OS and database environment")]
RDSCustom -->|Applications| LegacyApps[("Legacy & Custom Applications\n- Support for complex database setups")]
RDSCustom -->|Management| ManagedService[("Managed Service\n- Automated backups, patching, and recovery")]
RDSCustom -->|Control| RootAccess[("Root Access\n- For system-level changes")]
RDSCustom -->|Compatibility| Compatibility[("Compatibility\n- With existing AWS services")]
RDSCustom -->|Monitoring| EnhancedMonitoring[("Enhanced Monitoring\n- In-depth resource monitoring")]

    Customization -->|Database Parameters| DBParameters[("Database Parameters\n- Modify for specific workloads")]
    LegacyApps -->|Migration| MigrationSupport[("Migration Support\n- For on-premises databases")]
    ManagedService -->|Maintenance| AutomatedMaintenance[("Automated Maintenance\n- Retains high availability")]
    RootAccess -->|Custom Software| CustomSoftware[("Custom Software\n- Install and manage")]
    Compatibility -->|Integrations| ServiceIntegrations[("Service Integrations\n- Connect with other AWS services")]
    EnhancedMonitoring -->|Troubleshooting| Troubleshooting[("Troubleshooting\n- Advanced system metrics")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class RDSCustom,Customization,Applications,Management,Control,Compatibility,Monitoring important;
```

## Amazon RDS  vs Amazon RDS Custom
| Feature                          | Amazon RDS                                           | Amazon RDS Custom                                    |
|----------------------------------|-----------------------------------------------------|------------------------------------------------------|
| Management                       | Fully managed service                               | Managed service with customizable features           |
| Customization                    | Limited to specific DB parameters and settings      | Full control over the OS and database environment    |
| Root Access                      | Not available                                       | Available for system-level changes                   |
| Database Engine Support          | MySQL, PostgreSQL, MariaDB, Oracle, SQL Server      | Oracle, SQL Server (with more to come)               |
| Operating System Access          | Managed by AWS                                      | Customer-managed, with AWS support                   |
| Maintenance                      | Automated patching and backups                      | Selective automated and manual patching and backups  |
| Application Suitability          | Standard applications and workloads                 | Legacy, custom, and packaged applications requiring specific configurations |
| Compatibility with AWS Services  | High                                               | High, but may vary based on customizations           |
| Monitoring                       | Standard RDS monitoring                             | Enhanced monitoring with access to OS-level metrics  |
| Hardware Access                  | Not available                                       | Available for specific use cases                     |
| Use Case                         | Turnkey solutions for common database requirements  | Complex environments needing customization           |
| Pricing                          | Standard RDS pricing                                | Additional cost for increased flexibility and control|


## RDS Backup Strategies
```mermaid
graph LR;
RDSBackup[("RDS Backup Strategies")]
RDSBackup -->|Automated Backups| AutomatedBackups[("Automated Backups\n- Daily full backup\n- Transaction logs every 5 minutes\n-")]
RDSBackup -->|Snapshots| ManualSnapshots[("DB Snapshots\n- User-initiated\n- Stored until manually deleted\n-")]
RDSBackup -->|Retention| BackupRetention[("Backup Retention Period\n- 1 to 35 days for automated backups\n-")]
RDSBackup -->|Recovery| PointInTimeRecovery[("Point-in-Time Recovery\n- To any second within retention period\n-")]
RDSBackup -->|Encryption| BackupEncryption[("Encryption\n- At rest using AWS KMS\n-")]
RDSBackup -->|Multi-Region| CrossRegionBackup[("Cross-Region Backup\n- For disaster recovery\n-")]
RDSBackup -->|Best Practices| BackupBestPractices[("Backup Best Practices\n- Regularly test recovery\n- Secure backup data\n-")]

    AutomatedBackups -->|Window| BackupWindow[("Backup Window\n- Set preferred backup window\n-")]
    ManualSnapshots -->|Consistency| SnapshotConsistency[("Consistent State\n- No need to stop DB\n-")]
    BackupRetention -->|Policy| RetentionPolicy[("Retention Policy\n- Configurable per DB\n-")]
    PointInTimeRecovery -->|Logs| TransactionLogs[("Transaction Logs\n- Enable specific time recovery\n-")]
    BackupEncryption -->|Key Management| KeyManagement[("Key Management\n- Use customer-managed keys for enhanced control\n-")]
    CrossRegionBackup -->|Replication| BackupReplication[("Replication\n- Automatic or manua\n-l")]
    BackupBestPractices -->|Documentation| Documentation[("Documentation\n- Maintain backup policies documentation\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class RDSBackup,AutomatedBackups,Snapshots,Retention,Recovery,Encryption,Multi-Region,BestPractices important;
```


## Differences between snapshots and backups on Amazon RDS

| Feature                    | RDS Snapshot                              | RDS Automated Backup                       |
|----------------------------|-------------------------------------------|--------------------------------------------|
| Type of Operation          | Manual or automatic (if triggered by user)| Automated by AWS RDS                       |
| Frequency                  | On-demand                                 | Daily, plus transaction logs every 5 minutes|
| Retention Period           | User-defined, can be indefinite           | 1 to 35 days (user-configurable)           |
| Restoration Time           | Might be longer due to larger data size   | Generally faster due to incremental nature |
| Point-in-Time Recovery     | Not available                             | Available within the retention period      |
| Storage Location           | Amazon S3                                 | Amazon S3                                  |
| Availability               | Available for all RDS engines             | Available for all RDS engines              |
| Storage Costs              | Based on the amount of data stored        | Included in RDS pricing; additional storage costs for logs|
| Impact on Performance      | Minimal, if any                           | Minimal, due to continuous backup          |
| Use Case                   | Long-term storage, archiving, or migration| Quick recovery, operational restores       |



## For exam

1. A healthcare company uses its on-premises infrastructure to run legacy applications that require specialized customizations to the underlying Oracle database as well as its host operating system (OS). The company also wants to improve the availability of the Oracle database layer. The company has hired you as an AWS Certified Solutions Architect – Associate to build a solution on AWS that meets these requirements while minimizing the underlying infrastructure maintenance effort.

Which of the following options represents the best solution for this use case?

***Answer*** Leverage multi-AZ configuration of Amazon RDS Custom for Oracle that allows the Database Administrator (DBA) to access and customize the database environment and the underlying operating system

Amazon RDS is a managed service that makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while managing time-consuming database administration tasks. Amazon RDS can automatically back up your database and keep your database software up to date with the latest version. However, RDS does not allow you to access the host OS of the database.

For the given use-case, you need to use Amazon RDS Custom for Oracle as it allows you to access and customize your database server host and operating system, for example by applying special patches and changing the database software settings to support third-party applications that require privileged access. Amazon RDS Custom for Oracle facilitates these functionalities with minimum infrastructure maintenance effort. You need to set up the RDS Custom for Oracle in multi-AZ configuration for high availability.

```mermaid
graph LR
    A[Solution for Healthcare Company's Oracle Database] --> B[Leverage Amazon RDS Custom for Oracle]
    A --> C[Implement Multi-AZ Configuration for High Availability]
    A --> D[Minimize Infrastructure Maintenance Effort]

    B --> E[Access and Customize Database Environment]
    B --> F[Customize Underlying Operating System]
    B --> G[Support for Specialized Customizations]

    C --> H[Automatic Failover]
    C --> I[Synchronous Data Replication]
    C --> J[Increased Data Redundancy]

    D --> K[Managed Service Benefits]
    D --> L[Automated Backups and Updates]
    D --> M[Cost-Efficient and Resizable Capacity]

    A --> N[Comprehensive Solution for Legacy Applications]
    N --> O[Balanced Customization and Manageability]

```