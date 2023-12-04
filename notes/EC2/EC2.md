# EC2




```mermaid
graph LR
    A[EC2 Placement Group Strategies] --> B[Cluster Strategy]
    A --> C[Spread Strategy]
    A --> D[Partition Strategy]

    B --> E[Low-Latency Group in Single AZ]
    B --> F[High Network Throughput]
    B --> G[All Instances in Same AZ]

    C --> H[Spreads Instances Across Hardware]
    C --> I[Reduce Hardware Failure Risks]
    C --> J[Up to 7 Instances per AZ]

    D --> K[Spreads Across Partitions in an AZ]
    D --> L[Logical Groupings in AZ]
    D --> M[Isolated Network and Power Domains]
    D --> N[Suited for Hadoop, Cassandra, Kafka]

    A --> O[Key Decision for Workload Deployment]
    O --> P[Based on Performance and Resiliency Needs]

```

```mermaid
graph LR
    A[Cluster Placement Group in Amazon EC2] --> B[Pros]
    A --> C[Cons]
    A --> D[Use Cases]

    B --> E[Great Network Performance]
    B --> F[Up to 10 Gbps Bandwidth]
    B --> G[Beneficial for High-Throughput or Low-Latency Access]

    C --> H[Risk of Simultaneous Failure]
    C --> I[Instances Located on Same Rack]

    D --> J[Ideal for Big Data Jobs]
    D --> K[Interdependent Tasks, Require Fast Communication]
    D --> L[Suited for High-Performance Computing HPC]
    D --> M[Real-time Data Processing Workloads]

    A --> N[Visual Representation]
    N --> O[Proximity within Same Rack and AZ]
    O --> P[Low Latency and High Bandwidth Connectivity]

```


```mermaid
graph LR
    A[Spread Placement Groups in AWS EC2] --> B[Pros]
    A --> C[Cons]
    A --> D[Use Cases]

    B --> E[Span Across Multiple AZs]
    B --> F[Reduced Risk of Simultaneous Failure]
    B --> G[Instances Isolated on Different Physical Hardware]

    C --> H[Limit of 7 Instances per AZ per Group]
    C --> I[Not Suitable for Large Scale Deployments]

    D --> J[Ideal for High Availability Applications]
    D --> K[Maximize Fault Tolerance]
    D --> L[Beneficial for Critical Applications]
    D --> M[Isolation and Protection from Failures]

    A --> N[Visual Representation]
    N --> O[Instances Spread Across Hardware in AZs]
    O --> P[Minimizing Risk and Maximizing Availability]

```

```mermaid
graph LR
    A[Partition Placement Groups in AWS] --> B[Features]
    A --> C[Instance Isolation]
    A --> D[Resilience]
    A --> E[Metadata Access]
    A --> F[Use Cases]

    B --> G[Up to 7 Partitions per AZ]
    B --> H[Extend Across Multiple AZs]
    B --> I[Supports Hundreds of Instances per Group]

    C --> J[No Shared Hardware Across Partitions]
    D --> K[Failure in One Partition Doesn't Impact Others]
    E --> L[Access to Partition Information in Metadata]

    F --> M[High Availability Workloads]
    F --> N[Distributed File Systems e.g., HDFS]
    F --> O[NoSQL Databases e.g., Cassandra]
    F --> P[Message Brokers e.g., Kafka]

    A --> Q[Visual Representation]
    Q --> R[Instances Grouped in Partitions]
    Q --> S[Spread Across Different AZs]
    S --> T[Emphasizing Isolation and Fault Tolerance]

```



```mermaid
graph LR;
    EC2Metadata[("EC2 Instance Metadata Service")]
    EC2Metadata -->|Purpose| Purpose[("Provides information about running EC2 instances")]
    EC2Metadata -->|Access| Access[("Accessible at http://169.254.169.254/latest/meta-data/")]
    EC2Metadata -->|Data Provided| DataProvided[("Includes details like instance ID, AMI ID, network, and security groups")]
    EC2Metadata -->|Use Cases| UseCases[("Used for configuring or managing the running instance")]
    EC2Metadata -->|Security| Security[("Access restricted to the EC2 instance itself")]
    EC2Metadata -->|Versioning| Versioning[("Supports IMDSv1 (open) and IMDSv2 (session-oriented)")]
    EC2Metadata -->|Temporary Credentials| TempCredentials[("Can retrieve IAM role credentials for the instance")]
    EC2Metadata -->|Dynamic Data| DynamicData[("Also provides dynamic data about instances")]

    classDef classSection fill:#f9a,stroke:#333,stroke-width:2px;
    class EC2Metadata,Purpose,Access,DataProvided,UseCases,Security,Versioning,TempCredentials,DynamicData classSection;

```



## For exam

1. A company has a web application that runs 24*7 in the production environment. The development team at the company runs a clone of the same application in the dev environment for up to 8 hours every day. The company wants to build the MOST cost-optimal solution by deploying these applications using the best-fit pricing options for Amazon Elastic Compute Cloud (Amazon EC2) instances.

What would you recommend?

***Answer:*** For the given use case, you can use Amazon EC2 Reserved Instances for the production application as it is run 24*7. This way you can get a 72% discount if you avail a 3-year term. You can use on-demand instances for the dev application since it is only used for up to 8 hours per day. On-demand offers the flexibility to only pay for the Amazon EC2 instance when it is being used (0 to 8 hours for the given use case).


```mermaid
graph LR
    A[Cost-Optimal Deployment for Web Applications] --> B[Production Environment Application]
    A --> C[Development Environment Application]

    B --> D[Use Amazon EC2 Reserved Instances]
    C --> E[Use Amazon EC2 On-Demand Instances]

    D --> F[Run 24*7]
    D --> G[Avail 72% Discount with 3-year Term]

    E --> H[Run up to 8 Hours per Day]
    E --> I[Pay Only When Used]

    A --> J[Recommended Strategy]
    J --> K[Reserved Instances for Continuous Use]
    J --> L[On-Demand for Flexible Use]

```


2. A company manages a multi-tier social media application that runs on Amazon Elastic Compute Cloud (Amazon EC2) instances behind an Application Load Balancer. The instances run in an Amazon EC2 Auto Scaling group across multiple Availability Zones (AZs) and use an Amazon Aurora database. As an AWS Certified Solutions Architect – Associate, you have been tasked to make the application more resilient to periodic spikes in request rates.

Which of the following solutions would you recommend for the given use-case? (Select two)

***Answer*** Correct options:

You can use Amazon Aurora replicas and Amazon CloudFront distribution to make the application more resilient to spikes in request rates.

Use Amazon Aurora Replica

Amazon Aurora Replicas have two main purposes. You can issue queries to them to scale the read operations for your application. You typically do so by connecting to the reader endpoint of the cluster. That way, Aurora can spread the load for read-only connections across as many Aurora Replicas as you have in the cluster. Amazon Aurora Replicas also help to increase availability. If the writer instance in a cluster becomes unavailable, Aurora automatically promotes one of the reader instances to take its place as the new writer. Up to 15 Aurora Replicas can be distributed across the Availability Zones (AZs) that a DB cluster spans within an AWS Region.

Use Amazon CloudFront distribution in front of the Application Load Balancer

Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment. CloudFront points of presence (POPs) (edge locations) make sure that popular content can be served quickly to your viewers. Amazon CloudFront also has regional edge caches that bring more of your content closer to your viewers, even when the content is not popular enough to stay at a POP, to help improve performance for that content.

Amazon CloudFront offers an origin failover feature to help support your data resiliency needs. Amazon CloudFront is a global service that delivers your content through a worldwide network of data centers called edge locations or points of presence (POPs). If your content is not already cached in an edge location, Amazon CloudFront retrieves it from an origin that you've identified as the source for the definitive version of the content.


```mermaid
graph LR
    A[Enhancing Resilience to Request Rate Spikes in Social Media Application] --> B[Use Amazon Aurora Replica]
    A --> C[Use Amazon CloudFront Distribution]

    B --> D[Scale Read Operations]
    B --> E[Increase Availability]
    B --> F[Distributed Across AZs]

    D --> G[Query Replicas for Read-Only Connections]
    E --> H[Automatic Promotion of Reader Instance as Writer]
    F --> I[Up to 15 Replicas per Region]

    C --> J[Fast Content Delivery Network]
    C --> K[Origin Failover Feature]
    C --> L[Global Network of Data Centers]

    J --> M[Secure Data and Application Delivery]
    J --> N[Low Latency, High Transfer Speeds]
    K --> O[Supports Data Resiliency]
    L --> P[Improved Performance for Content Delivery]

    A --> Q[Recommendations as AWS Certified Solutions Architect]
    Q --> R[Optimize for Spikes in Traffic]
    R --> S[Balance Load and Ensure High Availability]

```


3. The solo founder at a tech startup has just created a brand new AWS account. The founder has provisioned an Amazon EC2 instance 1A which is running in AWS Region A. Later, he takes a snapshot of the instance 1A and then creates a new Amazon Machine Image (AMI) in Region A from this snapshot. This AMI is then copied into another Region B. The founder provisions an instance 1B in Region B using this new AMI in Region B.

At this point in time, what entities exist in Region B?

***Answer:*** Correct option:

1 Amazon EC2 instance, 1 AMI and 1 snapshot exist in Region B

An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. When the new AMI is copied from Region A into Region B, it automatically creates a snapshot in Region B because AMIs are based on the underlying snapshots. Further, an instance is created from this AMI in Region B. Hence, we have 1 Amazon EC2 instance, 1 AMI and 1 snapshot in Region B.

```mermaid
graph TD
    A[Entities in AWS Region B] --> B[1 Amazon EC2 Instance]
    A --> C[1 Amazon Machine Image AMI]
    A --> D[1 Snapshot]

    B --> E[Instance 1B Provisioned Using AMI]
    C --> F[AMI Copied from Region A]
    D --> G[Snapshot Created Automatically with AMI]

    A --> H[Result of Tech Startup Founder's Actions]
    H --> I[Snapshot and AMI Created from EC2 Instance 1A in Region A]
    I --> J[AMI and Snapshot Required for EC2 Instance]

```


4. An ivy-league university is assisting NASA to find potential landing sites for exploration vehicles of unmanned missions to our neighboring planets. The university uses High Performance Computing (HPC) driven application architecture to identify these landing sites.

Which of the following Amazon EC2 instance topologies should this application be deployed on?

***Answer:*** The Amazon EC2 instances should be deployed in a cluster placement group so that the underlying workload can benefit from low network latency and high network throughput

The key thing to understand in this question is that HPC workloads need to achieve low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of HPC applications. Cluster placement groups pack instances close together inside an Availability Zone. These are recommended for applications that benefit from low network latency, high network throughput, or both. Therefore this option is the correct answer.

```mermaid
graph LR
    A[EC2 Instance Topology for HPC Application] --> B[Deploy in Cluster Placement Group]
    A --> C[Requirement for Low Latency and High Throughput]

    B --> D[Instances Close Together in an AZ]
    B --> E[Benefit from Low Network Latency]
    B --> F[High Network Throughput]

    C --> G[Ideal for Tightly-Coupled Node-to-Node Communication]
    C --> H[Critical for HPC Workloads]

    A --> I[Application: Identify Planetary Landing Sites]
    I --> J[Need for Optimal HPC Performance]
    J --> K[Ensure Efficient Processing and Analysis]

    A --> L[Recommended for Ivy-League University's NASA Project]
    L --> M[Maximize Application Efficiency and Performance]

```