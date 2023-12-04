# Aurora

```mermaid
graph LR;
    Aurora[("AWS Aurora\n-")]
    Aurora -->|Performance| HighPerformance[("High Performance\n- Up to 5x performance of MySQL\n-")]
    Aurora -->|Scalability| AutoScaling[("Auto-scaling\n- Read replicas scale up to 15\n-")]
    Aurora -->|Availability| HighAvailability[("High Availability\n- Multi-AZ deployments with failover\n-")]
    Aurora -->|Durability| Durability[("Durability\n- 6-way replication across 3 AZs\n-")]
    Aurora -->|Maintenance| LessMaintenance[("Less Maintenance\n- Automated backups and patches\n-")]
    Aurora -->|Compatibility| Compatibility[("Compatibility\n- MySQL and PostgreSQL\n-")]
    Aurora -->|Security| SecurityFeatures[("Security\n- Encryption at rest and in transit\n-")]
    Aurora -->|Recovery| PointInTimeRecovery[("Point-in-time Recovery\n- Continuous backup to S3\n-")]

    HighPerformance -->|Read/Write Splitting| RWsplitting[("Read/Write Splitting\n- Improved read performance\n-")]
    AutoScaling -->|Read Replicas| ReadReplicas[("Read Replicas\n- Automated load balancing\n-")]
    HighAvailability -->|Instant Failover| InstantFailover[("Instant Failover\n- No manual intervention\n-")]
    Durability -->|Data Loss Protection| DataLossProtection[("Data Loss Protection\n- Distributed systems\n-")]
    LessMaintenance -->|Automated Tasks| AutomatedTasks[("Automated Tasks\n- Version upgrades\n-")]
    Compatibility -->|Drop-in Replacement| DropIn[("Drop-in Replacement\n- Easy migration from MySQL/PostgreSQL\n-")]
    SecurityFeatures -->|IAM| IAMIntegration[("IAM Integration\n- Advanced access control\n-")]
    Recovery -->|Backup and Restore| BackupRestore[("Backup and Restore\n- To new instances\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class Aurora,HighPerformance,AutoScaling,HighAvailability,Durability,LessMaintenance,Compatibility,SecurityFeatures,Recovery important;

```

## Amazon Aurora High Availability & Read Scaling
```mermaid
graph LR;
AuroraHA[("Amazon Aurora\nHigh Availability & Read Scaling\n-")]
AuroraHA -->|Fault Tolerance| MultiAZ[("Multi-AZ Deployment\n- Automatic failover\n-")]
AuroraHA -->|Data Durability| DataRedundancy[("Data Redundancy\n- 6-way replication across 3 AZs\n-")]
AuroraHA -->|Self Healing| SelfHealing[("Self-healing Storage\n- Disk failures are repaired automatically\n-")]
AuroraHA -->|Scaling| ReadReplicas[("Read Replicas\n- Up to 15 replicas for read scaling\n-")]
AuroraHA -->|Load Distribution| LoadBalancing[("Load Balancing\n- Reader endpoint for connection balancing\n-")]
AuroraHA -->|Promotion Speed| FastReplicaPromotion[("Fast Replica Promotion\n- Promote replicas to primary quickly\n-")]
AuroraHA -->|Data Backup| ContinuousBackup[("Continuous Backup\n- To Amazon S3\n-")]
AuroraHA -->|Failover Mechanism| AutoFailover[("Automated Failover\n- Instant redirection to replicas\n-")]
AuroraHA -->|Geographic Scaling| CrossRegionReplication[("Cross-Region Replication\n- For global applications\n-")]

    MultiAZ -->|Zero Downtime| NoDowntime[("No Downtime During Failover\n-")]
    DataRedundancy -->|No Data Loss| ZeroDataLoss[("Zero Data Loss\n- On database crash recovery\n-")]
    ReadReplicas -->|Read Traffic Handling| ScaleReads[("Handle Read Traffic\n- Evenly distribute reads\n-")]
    LoadBalancing -->|Endpoint Management| ReaderEndpoint[("Reader Endpoint\n- Distributes read traffic\n-")]
    ContinuousBackup -->|Recovery Point| PITRecovery[("Point-in-Time Recovery\n- Restore to any second\n-")]
    AutoFailover -->|High Availability| HA[("High Availability\n- Ensures database service continuity\n-")]
    CrossRegionReplication -->|Global DR| GlobalDR[("Global Disaster Recovery\n- Data available across regions\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraHA,MultiAZ,DataRedundancy,SelfHealing,ReadReplicas,LoadBalancing,FastReplicaPromotion,ContinuousBackup,AutoFailover,CrossRegionReplication important;
```

## Aurora Endpoints
```mermaid
graph LR;
AuroraEndpoints[("Aurora Endpoints\n-")]
AuroraEndpoints -->|Dedicated for writes| WriterEndpoint[("Writer Endpoint\n- Single, points to primary instance\n- Handles all write operations\n-")]
AuroraEndpoints -->|Balances read traffic| ReaderEndpoint[("Reader Endpoint\n- Load balances across read replicas\n- Supports read scaling\n-")]

    WriterEndpoint -->|Write Consistency| WriteConsistency[("Write Consistency\n- Ensures data integrity for writes\n-")]
    WriterEndpoint -->|Failover Support| WriterFailover[("Failover Support\n- Automatically fails over to a new primary instance\n-")]

    ReaderEndpoint -->|Read Scaling| ReadScaling[("Read Scaling\n- Distributes reads across multiple replicas\n-")]
    ReaderEndpoint -->|Connection Pooling| ReadConnectionPooling[("Connection Pooling\n- Improves efficiency of read traffic management\n-")]

    WriteConsistency -->|ACID Compliance| ACIDCompliance[("ACID Compliance\n- Transactions are reliably processed\n-")]
    WriterFailover -->|Automatic Promotion| AutoPromotion[("Automatic Promotion\n- Replica becomes new writer\n-")]

    ReadScaling -->|Replica Selection| ReplicaSelection[("Replica Selection\n- Redirects to the least loaded replica\n-")]
    ReadConnectionPooling -->|Maximize Throughput| MaxThroughput[("Maximize Throughput\n- Manages numerous concurrent read sessions\n-")]

    classDef endpoint fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraEndpoints,WriterEndpoint,ReaderEndpoint,WriteConsistency,WriterFailover,ReadScaling,ReadConnectionPooling endpoint;
```

## Aurora Read Replicas

```mermaid
graph LR;
AuroraReadReplicas[("Aurora Read Replicas\n-")]
AuroraReadReplicas -->|Purpose| ScalingReads[("Scaling Read Operations\n- Distribute query load\n-")]
AuroraReadReplicas -->|Availability| ImprovedAvailability[("Improved Availability\n- Additional nodes for failover\n-")]
AuroraReadReplicas -->|Performance| ReadPerformance[("Enhanced Read Performance\n- Can create up to 15 Read Replicas\n-")]
AuroraReadReplicas -->|Latency| ReducedLatency[("Reduced Latency\n- Replicas in different regions\n-")]
AuroraReadReplicas -->|Failover| AutomaticFailover[("Automatic Failover\n- To replica if the primary fails\n-")]
AuroraReadReplicas -->|Endpoints| ReaderEndpoint[("Reader Endpoint\n- Directs read traffic to replicas\n-")]
AuroraReadReplicas -->|Storage| SharedStorage[("Shared Storage Volume\n- Single distributed volume for all instances\n-")]

    ScalingReads -->|Load Balancing| LoadBalancing[("Load Balancing\n- Even distribution across replicas\n-")]
    ImprovedAvailability -->|Disaster Recovery| DisasterRecovery[("Disaster Recovery\n- Cross-region replication\n-")]
    ReadPerformance -->|Non-Blocking Reads| NonBlockingReads[("Non-Blocking Reads\n- Replicas lag minimally behind\n-")]
    ReducedLatency -->|Global Users| GlobalUsers[("Serve Global Users\n- Geographical proximity to users\n-")]
    AutomaticFailover -->|High Availability| HA[("High Availability\n- Ensures database service continuity\n-")]
    ReaderEndpoint -->|Connection Pooling| ConnectionPooling[("Connection Pooling\n- Efficient read connection management\n-")]
    SharedStorage -->|Data Durability| StorageDurability[("High Durability\n- 6 replicas across 3 AZs\n- automatically scales with the data from 10GB up to 128TB \n-")]
    SharedStorage -->|Continuous Backup| StorageBackup[("Continuous Backup\n- To Amazon S3\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraReadReplicas,ScalingReads,ImprovedAvailability,ReadPerformance,ReducedLatency,AutomaticFailover,Endpoints,SharedStorage important;

```


## Aurora Custom Endpoints

```mermaid
graph LR;
CustomEndpoints[("Aurora Custom Endpoints\n-")]
CustomEndpoints -->|Purpose| TrafficManagement[("Traffic Management\n- Direct traffic to designated replicas\n-")]
CustomEndpoints -->|Use Cases| UseCaseLoadBalancing[("Load Balancing\n- Custom load balancing for different workloads\n-")]
CustomEndpoints -->|Flexibility| InstanceTypeRouting[("Instance Type Routing\n- Route to instances with specific compute or memory\n-")]
CustomEndpoints -->|Performance| PerformanceOptimization[("Performance Optimization\n- Optimize for read/write operations\n-")]
CustomEndpoints -->|High Availability| HighAvailability[("High Availability\n- Prioritize traffic to healthy replicas\n-")]
CustomEndpoints -->|Customization| Customization[("Customization\n- Create endpoints for specific application needs\n-")]

    TrafficManagement -->|Traffic Splitting| TrafficSplitting[("Traffic Splitting\n- Split read/write loads\n-")]
    UseCaseLoadBalancing -->|Workload Isolation| WorkloadIsolation[("Workload Isolation\n- Separate reporting from transactional processing\n-")]
    InstanceTypeRouting -->|Efficiency| RoutingEfficiency[("Routing Efficiency\n- Efficient use of instance capabilities\n-")]
    PerformanceOptimization -->|Read/Write Splitting| ReadWriteSplitting[("Read/Write Splitting\n- Designate endpoints for specific types of queries\n-")]
    HighAvailability -->|Failover| FailoverStrategy[("Failover Strategy\n- Minimize downtime during outages\n-")]
    Customization -->|Application Specific| ApplicationEndpoints[("Application Specific Endpoints\n- Align with application architecture\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class CustomEndpoints,TrafficManagement,UseCaseLoadBalancing,InstanceTypeRouting,PerformanceOptimization,HighAvailability,Customization important;
```

## Amazon Aurora Multi-Master

```mermaid

graph LR;
AuroraMultiMaster[("Amazon Aurora Multi-Master\n-")]
AuroraMultiMaster -->|Purpose| MultiWrite[("Multiple Write Masters\n- Concurrent write operations across instances\n-")]
AuroraMultiMaster -->|Availability| IncreasedAvailability[("Increased Availability\n- No single point of failure for writes\n-")]
AuroraMultiMaster -->|Scalability| WriteScalability[("Write Scalability\n- Scale out write capacity\n-")]
AuroraMultiMaster -->|Deployment| MultiRegion[("Multi-Region Deployment\n- Global database with cross-region write availability\n-")]
AuroraMultiMaster -->|Conflict Resolution| ConflictHandling[("Conflict Resolution\n- Automated conflict detection and resolution\n-")]
AuroraMultiMaster -->|Use Cases| UseCases[("Use Cases\n- Systems requiring high write availability and cross-region disaster recovery\n-")]

    MultiWrite -->|Load Distribution| LoadDistribution[("Even Load Distribution\n- Distribute write load to avoid hotspots\n-")]
    IncreasedAvailability -->|Zero Downtime| ZeroDowntime[("Zero Downtime Failover\n- For write operations\n-")]
    WriteScalability -->|Performance| HighPerformance[("High Performance\n- Maintain performance under heavy write load\n-")]
    MultiRegion -->|Global Reach| GlobalReach[("Global Reach\n- Serve users from geographically closest region\n-")]
    ConflictHandling -->|Consistency| DataConsistency[("Data Consistency\n- Ensure data integrity across masters\n-")]
    UseCases -->|Critical Applications| CriticalApps[("Critical Applications\n- Financial, health systems, etc.\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraMultiMaster,MultiWrite,IncreasedAvailability,WriteScalability,MultiRegion,ConflictHandling,UseCases important;
```

## Amazon Aurora Global Database

```mermaid
graph LR;
AuroraGlobal[("Amazon Aurora Global Database\n-")]
AuroraGlobal -->|High Availability| HA[("Multi-Region Deployment\n- Enhanced availability & disaster recovery\n-")]
AuroraGlobal -->|Performance| LowLatency[("Low Latency Replication\n- Typically under 1 second\n-")]
AuroraGlobal -->|Disaster Recovery| DR[("Fast Regional Failover\n- RTO < 1 minute\n-")]
AuroraGlobal -->|Read Scaling| ReadReplicas[("Read Replicas\n- Up to 16 in each secondary region\n-")]
AuroraGlobal -->|Data Access| LocalReads[("Local Reads\n- Improve read performance across geographies\n-")]
AuroraGlobal -->|Operational Simplicity| SimpleManage[("Simple Management\n- Similar to managing a single-region Aurora DB\n-")]
AuroraGlobal -->|Cross-Region Operations| CrossRegionOps[("Cross-Region Operations\n- Maintain read/write operations during outages\n-")]

    HA -->|Redundancy| Redundancy[("Data Redundancy\n- Across regions\n-")]
    LowLatency -->|Real-time Applications| RealTime[("Supports Real-time Use Cases\n-")]
    DR -->|Promotion| Promotion[("Promote Secondary to Primary\n- For disaster recovery\n-")]
    ReadReplicas -->|Load Balancing| LoadBalancing[("Load Balancing Across Replicas\n-")]
    LocalReads -->|Reduced Latency| ReducedLatency[("Reduced Latency for Global Users\n-")]
    SimpleManage -->|Automated Tasks| Automation[("Automated Backups and Updates\n-")]
    CrossRegionOps -->|Continuous Operations| ContinuousOps[("Continuous Operations During Regional Failures\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraGlobal,HA,Performance,DisasterRecovery,ReadScaling,DataAccess,OperationalSimplicity,CrossRegionOps important;
```


## Amazon Aurora Backups

```mermaid
graph LR;
AuroraBackup[("Amazon Aurora Backups\n-")]
AuroraBackup -->|Automated Snapshots| AutomatedSnapshots[("Automated Snapshots\n- Continuous & incremental\n-")]
AuroraBackup -->|Manual Snapshots| ManualSnapshots[("Manual Snapshots\n- User-initiated at any time\n-")]
AuroraBackup -->|Backup Retention| BackupRetention[("Backup Retention\n- Default 1 day, up to 35 days\n-")]
AuroraBackup -->|Point-In-Time Recovery| PITRecovery[("Point-In-Time Recovery\n- Up to the last 5 minutes\n-")]
AuroraBackup -->|Encryption| BackupEncryption[("Encryption\n- At rest using AWS KMS, by default\n-")]
AuroraBackup -->|Cross-Region Copy| CrossRegionCopy[("Cross-Region Snapshot Copy\n- For disaster recovery\n-")]
AuroraBackup -->|Backtrack| BacktrackFeature[("Backtrack\n- Rewind without restoring snapshot\n-")]

    AutomatedSnapshots -->|Zero Impact| ZeroImpact[("Zero Performance Impact\n- No I/O suspension\n-")]
    ManualSnapshots -->|Long-Term Retention| LongTermRetention[("Long-Term Retention\n- Keep snapshots as long as needed\n-")]
    BackupRetention -->|Flexible Settings| FlexibleSettings[("Flexible Settings\n- Modify retention period\n-")]
    PITRecovery -->|Fine-Grained Restore| FineGrainedRestore[("Fine-Grained Restore\n- To precise point in time\n-")]
    BackupEncryption -->|Data Security| DataSecurity[("Data Security\n- AES-256 encryption\n-")]
    CrossRegionCopy -->|Global DR Strategy| GlobalDRStrategy[("Global DR Strategy\n- Maintain copy in multiple regions\n-")]
    BacktrackFeature -->|Operational Simplicity| OperationalSimplicity[("Operational Simplicity\n- Avoid full restores for small errors\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraBackup,AutomatedSnapshots,ManualSnapshots,BackupRetention,PITRecovery,BackupEncryption,CrossRegionCopy,BacktrackFeature important;
```


## Differences between restoring from a backup or snapshot versus using the backtrack feature on Amazon Aurora

| Feature                    | Restore from Backup/Snapshot                      | Backtracking in Amazon Aurora                       |
|----------------------------|--------------------------------------------------|-------------------------------------------------|
| Purpose                    | To recover data from a specific point in time     | To quickly undo accidental changes without restore |
| Time to Recover            | Can take several minutes to hours                 | Almost immediate, typically within seconds        |
| Downtime                   | Required; new instance creation involved          | None; operation is done in-place                  |
| Data Loss                  | No data loss if done correctly                    | Potential for minimal data loss                   |
| Availability               | All RDS database engines                          | Only available for Amazon Aurora                  |
| Point-in-Time              | Any point within the snapshot retention period    | Up to the last backtrack window configured        |
| Operation Complexity       | More complex; involves creating a new instance    | Simple; no new resources required                 |
| Impact on Performance      | No impact on the running instance                 | Minimal impact; allows normal operations to continue |
| Use Case                   | Disaster recovery, corruption recovery            | Quick recovery from user errors, logical errors   |
| Storage Impact             | Requires additional storage for the new instance  | No additional storage needed                      |

## Amazon Aurora Database Cloning

```mermaid
graph LR;
AuroraCloning[("Aurora Database Cloning\n-")]
AuroraCloning -->|Efficiency| FastCloning[("Fast Cloning\n- Clones created quickly regardless of size\n-")]
AuroraCloning -->|Cost Effectiveness| CostSaving[("Cost Saving\n- Pay only for additional storage used\n-")]
AuroraCloning -->|Data Isolation| DataIsolation[("Data Isolation\n- Clone is independent of the source\n-")]
AuroraCloning -->|Operational Simplicity| SimpleOperation[("Operational Simplicity\n- Easy to create and manage\n-")]
AuroraCloning -->|Use Cases| UseCases[("Use Cases\n- Testing, development, production scaling\n-")]
AuroraCloning -->|Performance| NoImpact[("No Performance Impact\n- On the source database during cloning\n-")]
AuroraCloning -->|Freshness| UpToDate[("Up-to-Date\n- Clone reflects source database at creation time\n-")]

    FastCloning -->|No Data Movement| NoDataMovement[("No Data Movement\n- Uses shared storage architecture\n-")]
    CostSaving -->|Storage Optimization| StorageOptimization[("Storage Optimization\n- Only changes are stored\n-")]
    DataIsolation -->|Changes| ChangesIndependent[("Changes Independent\n- Modifications do not affect source\n-")]
    SimpleOperation -->|User Interface| UserInterface[("User Interface\n- Via AWS Console or API calls\n-")]
    UseCases -->|Parallel Operations| ParallelOperations[("Parallel Operations\n- For different workloads on the clone\n-")]
    NoImpact -->|Zero Downtime| ZeroDowntime[("Zero Downtime\n- For the source database\n-")]
    UpToDate -->|Point in Time| PointInTime[("Point in Time\n- Accurate as of the clone creation\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class AuroraCloning,FastCloning,CostSaving,DataIsolation,SimpleOperation,UseCases,NoImpact,UpToDate important;
```


## Amazon RDS & Aurora Security
```mermaid
graph LR;
    RDSSecurity[("Amazon RDS & Aurora Security\n-")]
    RDSSecurity -->|Encryption| AtRestEncryption[("Encryption at Rest\n- Uses AWS KMS\n-")]
    RDSSecurity -->|In-Transit Encryption| TransitEncryption[("Encryption in Transit\n- SSL/TLS\n-")]
    RDSSecurity -->|Access Control| IAMAuthentication[("IAM Authentication\n- Manage database access\n-")]
    RDSSecurity -->|Network Isolation| VPC[("VPC\n- Isolate database in private network\n-")]
    RDSSecurity -->|Monitoring| Monitoring[("Monitoring & Logging\n- CloudWatch & CloudTrail integration\n-")]
    RDSSecurity -->|Compliance| ComplianceCertification[("Compliance Certifications\n- HIPAA, GDPR, etc.\n-")]
    RDSSecurity -->|Patch Management| PatchManagement[("Automated Patch Management\n- Regularly updates for security\n-")]

    AtRestEncryption -->|Key Management| KMSIntegration[("KMS Integration\n- Control and audit key use\n-")]
    TransitEncryption -->|Certificate Management| CertificateManagement[("Certificate Management\n- Rotate SSL/TLS certificates\n-")]
    IAMAuthentication -->|Authentication| AuthenticationMechanism[("Authentication Mechanism\n- Token-based authentication\n-")]
    VPC -->|Security Groups| SecurityGroups[("Security Groups\n- Fine-grained ingress/egress rules\n-")]
    Monitoring -->|Alerts| Alerts[("Alerts\n- Set up for abnormal activities\n-")]
    ComplianceCertification -->|Best Practices| SecurityBestPractices[("Security Best Practices\n- Align with compliance requirements\n-")]
    PatchManagement -->|Update Schedule| UpdateSchedule[("Update Schedule\n- Define maintenance windows\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class RDSSecurity,AtRestEncryption,TransitEncryption,IAMAuthentication,VPC,Monitoring,ComplianceCertification,PatchManagement important;
```

## Amazon RDS Proxy
```mermaid
graph LR;
    RDSProxy[("Amazon RDS Proxy\n-")]
    RDSProxy -->|Connection Pooling| Pooling[("Connection Pooling\n- Reduces database load\n-")]
    RDSProxy -->|High Availability| HA[("High Availability\n- Automatic failover support\n-")]
    RDSProxy -->|Scalability| Scalability[("Scalability\n- Handles thousands of connections\n-")]
    RDSProxy -->|Latency| ReducedLatency[("Reduced Latency\n- Improves application responsiveness\n-")]
    RDSProxy -->|Security| Security[("Security\n- IAM authentication & SSL encryption\n-")]
    RDSProxy -->|Failover Handling| FailoverHandling[("Failover Handling\n- Seamless redirection to standby\n-")]
    RDSProxy -->|Monitoring| Monitoring[("Monitoring\n- Detailed metrics and logging\n-")]

    Pooling -->|Efficiency| Efficiency[("Efficiency\n- Reuses and manages connections\n-")]
    HA -->|Multi-AZ| MultiAZ[("Multi-AZ Deployment\n- Continuous operation across AZs\n-")]
    Scalability -->|Burst Traffic| BurstHandling[("Burst Traffic Handling\n- Manages sudden spikes\n-")]
    ReducedLatency -->|Query Caching| QueryCaching[("Query Caching\n- Cache frequent queries\n-")]
    Security -->|Secrets Management| SecretsManager[("Secrets Management\n- Integrates with AWS Secrets Manager\n-")]
    FailoverHandling -->|Transaction Replay| TransactionReplay[("Transaction Replay\n- Maintains consistency\n-")]
    Monitoring -->|Integration| Integration[("CloudWatch Integration\n- Logs and metrics for analysis\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class RDSProxy,Pooling,HA,Scalability,ReducedLatency,Security,FailoverHandling,Monitoring important;

```



## For exam
1. The flagship application for a gaming company connects to an Amazon Aurora database and the entire technology stack is currently deployed in the United States. Now, the company has plans to expand to Europe and Asia for its operations. It needs the games table to be accessible globally but needs the users and games_played tables to be regional only.

How would you implement this with minimal application refactoring?


***Answer*** : Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 128TB per database instance. Aurora is not an in-memory database.

Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages. Amazon Aurora Global Database is the correct choice for the given use-case.

For the given use-case, we, therefore, need to have two Aurora clusters, one for the global table (games table) and the other one for the local tables (users and games_played tables).


```mermaid
graph LR
    A[Strategy: Amazon Aurora for Gaming Company] --> B[1. Amazon Aurora Global Databases]
    A --> C[2. Regional Aurora Databases]
    A --> D[3. Application Layer Configuration]
    A --> E[4. Minimal Refactoring]
    A --> F[5. Monitoring and Optimization]
    A --> G[6. Security and Compliance]
    A --> H[Conclusion]

    B --> I[Global Database for 'games' Table]
    B --> J[Primary Region with All Tables]
    B --> K[Secondary Regions with 'games' Replication]

    C --> L[Separate Databases for 'users', 'games_played']
    C --> M[Data Isolation in Regions]

    D --> N[Global Access to 'games']
    D --> O[Regional Access for Other Tables]

    E --> P[Connection Routing in Application]
    E --> Q[Data Consistency Across Regions]

    F --> R[Performance Monitoring with CloudWatch]
    F --> S[Scalability Based on Traffic and Demand]

    G --> T[Data Protection: Encryption]
    G --> U[Compliance with Data Protection Laws]

    H --> V[Efficient Global and Regional Data Access]
    H --> W[Minimized Application Refactoring]
    H --> X[Adherence to Expansion Plans]

```


2. A gaming company uses Amazon Aurora as its primary database service. The company has now deployed 5 multi-AZ read replicas to increase the read throughput and for use as failover target. The replicas have been assigned the following failover priority tiers and corresponding instance sizes are given in parentheses: tier-1 (16 terabytes), tier-1 (32 terabytes), tier-10 (16 terabytes), tier-15 (16 terabytes), tier-15 (32 terabytes).

In the event of a failover, Amazon Aurora will promote which of the following read replicas?

***Answer:*** Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 128TB per database instance. It delivers high performance and availability with up to 15 low-latency read replicas, point-in-time recovery, continuous backup to Amazon S3, and replication across three Availability Zones (AZs).

For Amazon Aurora, each Read Replica is associated with a priority tier (0-15). In the event of a failover, Amazon Aurora will promote the Read Replica that has the highest priority (the lowest numbered tier). If two or more Aurora Replicas share the same priority, then Amazon RDS promotes the replica that is largest in size. If two or more Aurora Replicas share the same priority and size, then Amazon Aurora promotes an arbitrary replica in the same promotion tier.

Therefore, for this problem statement, the Tier-1 (32 terabytes) replica will be promoted.

```mermaid
graph TD
    A[Amazon Aurora Failover Mechanism] --> B[Read Replica Priorities]
    A --> C[Failover Scenario]

    B --> D[Tier-1 16TB]
    B --> E[Tier-1 32TB]
    B --> F[Tier-10 16TB]
    B --> G[Tier-15 16TB]
    B --> H[Tier-15 32TB]

    C --> I[Promotion of Highest Priority Replica]
    C --> J[Selection Criteria in Same Priority]

    I --> K[Tier-1 Replica is Highest Priority]
    J --> L[Choose Largest Size in Same Tier]

    A --> M[In Event of Failover]
    M --> N[Promotion of Tier-1 32TB Replica]

```