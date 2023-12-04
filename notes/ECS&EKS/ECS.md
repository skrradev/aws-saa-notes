# ECS

## Amazon ECS EC2 Launch Type

```mermaid
graph LR
    A[Amazon ECS EC2 Launch Type] --> B[ECS - Elastic Container Service]
    B --> C[Docker Containers on AWS]
    C --> D[Define Tasks and Services]
    A --> E[EC2 Launch Type]
    E --> F[Manual Provisioning of EC2 Instances]
    F --> G[Control Over Instance Types and Scaling]
    A --> H[ECS Agent on Each EC2 Instance]
    H --> I[Manages Container Registration and Operations]
    A --> J[ECS Tasks and Clusters]
    J --> K[Define Container Groups]
    K --> L[Logical Groupings of EC2 Instances]
    A --> M[AWS Management]
    M --> N[Automates Container Start/Stop Based on Tasks]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,E,H,J,M subheading;
    class C,D,F,G,I,K,L,N details;


```

## Amazon ECS Fargate Launch Type

```mermaid

graph LR
A[Amazon ECS Fargate Launch Type] --> B[ECS - Elastic Container Service]
B --> C[Docker Containers on AWS]
A --> D[Fargate Launch Type]
D --> E[No EC2 Instance Management]
E --> F[Serverless Infrastructure]
A --> G[Task Definitions]
G --> H[Define Container Specs and Settings]
A --> I[Running ECS Tasks on Fargate]
I --> J[Managed CPU and RAM Allocation]
A --> K[Scaling]
K --> L[Scale Tasks, Not Servers]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,D,G,I,K subheading;
    class C,E,F,H,J,L details;
```

## IAM Roles for Amazon ECS - EC2 Launch Type

```mermaid
graph LR
A[IAM Roles for Amazon ECS - EC2 Launch Type] --> B[EC2 Instance Profile]
B --> C[Container Role for ECS Agent]
C --> D[Permissions for ECS Service Calls and AWS Resources]
A --> E[ECS Task Role]
E --> F[Assigned to ECS Tasks]
F --> G[Specific Permissions for Each Task]
A --> H[Task Definition]
H --> I[Defines Containers and Task Settings]
I --> J[Includes IAM Roles for Tasks]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,E,H subheading;
    class C,D,F,G,I,J details;

```


| Feature               | EC2 Instance Profile                                                                                             | ECS Task Role                                                                                                          |
|-----------------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| Purpose               | Provides permissions to the EC2 instance to allow the ECS agent to manage the containers.                        | Provides permissions to the ECS task itself, allowing each task to interact with AWS services according to its needs.  |
| Scope                 | Applies to the EC2 instance level.                                                                               | Applies to the task level, affecting all containers within the task.                                                   |
| Permissions           | Generally broader, used for instance management tasks such as registering with the ECS cluster.                  | More granular, intended for specific AWS service interactions required by the task.                                    |
| Defined In            | Associated with the EC2 instance itself.                                                                         | Defined within the ECS task definition.                                                                                |
| Used By               | ECS Agent running on the EC2 instance.                                                                           | Individual tasks and containers launched by ECS.                                                                       |
| Typical Actions       | Register the instance with the ECS cluster, send logs to CloudWatch, pull images from ECR.                       | Access S3 buckets, write to DynamoDB tables, publish messages to SNS topics, etc.                                      |
| Assumed By            | The ECS agent when making calls to AWS services on behalf of the EC2 instance.                                   | The ECS service when the task makes calls to AWS services.                                                             |
| Flexibility           | Less flexible as it applies the same role to all tasks on the instance.                                          | More flexible, allows different tasks to have different roles.                                                         |
| Best Used For         | Instances that need to perform administrative actions on the cluster or other AWS services.                       | Tasks that require specific AWS access without granting broad permissions to the underlying infrastructure.            |


## Amazon ECS Load Balancers

```mermaid
graph LR
A[Amazon ECS Load Balancers] --> B[Application Load Balancer ALB]
B --> C[Layer 7: HTTP/HTTPS Traffic]
C --> D[Advanced Request Routing for Microservices]

    A --> E[Network Load Balancer NLB]
    E --> F[Layer 4: IP Protocol Data]
    F --> G[Optimized for High Throughput and Low Latency]
    
    A --> H[Elastic Load Balancer Classic]
    H --> I[Previous Generation]
    I --> J[Basic Load Balancing at Request and Connection Level, Not recommended]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,E,H subheading;
    class C,D,F,G,I,J details;
```

## Amazon ECS with EFS
```mermaid
graph TD
    A[Amazon ECS with EFS] -->|Mounts EFS File System| B[ECS Tasks]
    B --> C[Shared and Persistent Storage Across Tasks]
    A --> D[EFS File System]
    D --> E[Regional Service with Multi-AZ Accessibility]
    E --> F[Highly Available and Scalable Storage]
    D --> G[Automatic Scaling without Provisioning]
    B --> H[Mounting Volumes for Containers]
    H --> I[Similar to Local File System]
    F --> J[Use Cases: CMS, Data Processing, Shared State]
    K[Note: Amazon S3 is an Object Store and cannot be mounted as a traditional file system like EFS]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;
    classDef usecase fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef note fill:#f2f2f2,stroke:#333,stroke-width:1px;

    class A heading;
    class B,D subheading;
    class E,F,G,H,I details;
    class J usecase;
    class K note;

```

## Capacity Providers in Amazon ECS
```mermaid
graph LR
A[Capacity Providers in Amazon ECS] --> B[FARGATE]
A --> C[FARGATE_SPOT]
A --> D[Infra ECS Cluster ]

    B --> E[Serverless Compute Engine for Containers]
    B --> F[No Need to Provision or Manage Servers]
    C --> G[Use of Fargate with Spot Pricing]
    C --> H[Discounted Rate, Possibility of Interruption]
    D --> I[Auto Scaling Group as Capacity Provider]
    D --> J[Automatically Adjusts Compute Capacity]

    E --> K[Type: FargateProvider]
    I --> L[Type: ASGProvider]
    J --> M[ASG: Infra ECS Cluster ]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef details fill:#ffffcc,stroke:#333,stroke-width:2px;
    classDef type fill:#ccffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,C,D subheading;
    class E,F,G,H,I,J details;
    class K,L,M type;
```


## Auto Scaling in Amazon ECS
```mermaid
graph LR
A[Auto Scaling in Amazon ECS] --> B[ECS Service Auto Scaling]
A --> C[AWS Application Auto Scaling]
A --> D[Scaling Strategies]
A --> E[Distinction Between ECS Service Auto Scaling and EC2 Auto Scaling]
A --> F[Fargate Auto Scaling]

    B --> B1[Automatically Adjusts Number of ECS Tasks]
    B1 --> B2[Based on Application Demand Patterns]

    C --> C1[Based on Various Metrics]
    C1 --> C2[Average CPU Utilization]
    C1 --> C3[Average Memory Utilization]
    C1 --> C4[ALB Request Count Per Target]

    D --> D1[Target Tracking]
    D --> D2[Step Scaling]
    D --> D3[Scheduled Scaling]
    D1 --> D1a[Based on CloudWatch Metric Target]
    D2 --> D2a[Defined Scaling Adjustments]
    D3 --> D3a[Scales Based on Schedule]

    E --> E1[ECS Service Auto Scaling: For ECS Tasks]
    E --> E2[EC2 Auto Scaling: For EC2 Instances]

    F --> F1[Easier Setup, Serverless Model]
    F1 --> F2[No Direct EC2 Instance Management]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef step fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,C,D,E,F subheading;
    class B1,B2,C1,C2,C3,C4,D1,D2,D3,D1a,D2a,D3a,E1,E2,F1,F2 step;
```

## EC2 Launch Type in ECS Auto Scaling EC2 Instances
```mermaid
graph LR
A[EC2 Launch Type in ECS] --> B[Auto Scaling EC2 Instances]
A --> C[Auto Scaling Group Scaling]
A --> D[ECS Cluster Capacity Provider]

    B --> B1[Based on ECS Service Demands]
    B1 --> B2[Scale Number of EC2 Instances]

    C --> C1[Configure Auto Scaling Group ASG]
    C1 --> C2[Adjust EC2 Instances Based on Metrics]
    C2 --> C3[CPU Utilization, Memory, etc.]

    D --> D1[Links ASG with ECS Cluster]
    D1 --> D2[Automatic Provisioning & Scaling]
    D2 --> D3[Signals ASG to Add More EC2 Instances as Needed]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef step fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,C,D subheading;
    class B1,B2,C1,C2,C3,D1,D2,D3 step;
    
```



| Feature                     | EC2 ASG (Auto Scaling Groups) | ECS Service Auto Scaling       | Fargate Auto Scaling           |
|-----------------------------|-------------------------------|--------------------------------|--------------------------------|
| Scaling Target              | EC2 Instances                 | ECS Tasks                      | ECS Tasks                      |
| Scaling Metrics             | CPU, Network, Custom          | CPU, Memory, Custom            | CPU, Memory, Custom            |
| Infrastructure Management   | Manual (by user)              | Managed by ECS                 | Serverless, fully managed by AWS|
| Pricing                     | Per EC2 instance hour         | Per task running               | Per task running               |
| Availability                | Multiple AZs                  | Multiple AZs                   | Multiple AZs                   |
| Integration with Load Balancer | Yes                         | Yes                            | Yes                            |
| Use Case                    | General purpose EC2 workloads | Containerized workloads        | Containerized workloads        |
| Failover Support            | Yes, via AZs and health checks| Yes, via task health checks    | Yes, via task health checks    |
| Granularity                 | Instance level                | Task (container) level         | Task (container) level         |
| Scalability                 | Manual scaling rules          | Automatic task scaling         | Automatic task scaling         |
| Server Management           | Required                      | Not required                   | Not required                   |
| Spot Instance Support       | Yes                           | Yes (if using EC2 launch type) | Yes (with Fargate Spot)        |


## CloudWatch Metric: ECS Service CPU Usage
```mermaid
graph LR
A[CloudWatch Metric: ECS Service CPU Usage] --> B[CloudWatch Alarm Triggered]
B --> C[Auto Scaling Response]

    C --> D[Auto Scaling Group ASG Actions]
    D --> D1[Launch EC2 Instances for Increased Capacity]
    D --> D2[Terminate EC2 Instances to Reduce Capacity]

    C --> E[Scale ECS Capacity Providers Optional]
    E --> E1[Scale Out: Add More ECS Tasks]
    E --> E2[Scale In: Remove ECS Tasks]

    F[ECS Tasks Management]
    F --> F1[Monitor and Manage Running Tasks]
    F --> F2[Start New Tasks for Additional Load]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef subheading fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef step fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A heading;
    class B,C subheading;
    class D,D1,D2,E,E1,E2,F,F1,F2 step;
    
```

## Upload Object to S3
```mermaid
graph TD
A[Upload Object to S3] -->|Triggers event| B[S3 Bucket]

    B -->|Event generated| C[Amazon EventBridge]
    C -->|Rule matched| D[Run ECS Task]

    D --> E[Amazon ECS Cluster]
    E -->|Start new task| F[Task new]
    F -->|Uses ECS Task Role| G[Access AWS Resources]

    G -->|Retrieve Object| B
    G -->|Save Result| H[Amazon DynamoDB]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef process fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef action fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A,B,C,D,E,F,G,H process;
```

## Amazon EventBridge
```mermaid
graph LR
A[Amazon EventBridge] -->|Every 1 hour| B[Rule: Run ECS Task]
B --> C[AWS Fargate]
C --> D[Task new]
D -->|Uses ECS Task Role| E[Access AWS Resources]

    E -->|Batch Processing| F[Amazon S3]
    E -->|Operates in| G[Amazon ECS Cluster]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef process fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef action fill:#ffffcc,stroke:#333,stroke-width:2px;

    class A,B,C,D,E,F,G process;

```

## ECR Role
```mermaid
graph TD
A[IAM Role] -->|Grants Pull Permissions| B[EC2 Instance]
B -->|Part of| C[ECS Cluster]
C -->|Pull Operation| D[ECR Repository]
D -->|Stores| E[Docker Images]
E -->|Backed by| F[Amazon S3]
E -->|Access Control via| A
E -->|Image Scanning & Lifecycle Management| G[ECR Features]
H[Public and Private Repositories] -->|Hosted in| D

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef role fill:#ff9999,stroke:#333,stroke-width:2px;
    classDef instance fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef cluster fill:#99ccff,stroke:#333,stroke-width:2px;
    classDef repository fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef image fill:#ffffcc,stroke:#333,stroke-width:2px;
    classDef s3 fill:#ccccff,stroke:#333,stroke-width:2px;
    classDef features fill:#ccffff,stroke:#333,stroke-width:2px;
    classDef repoType fill:#cccccc,stroke:#333,stroke-width:2px;

    class A role;
    class B instance;
    class C cluster;
    class D repository;
    class E image;
    class F s3;
    class G features;
    class H repoType;

```


| ECS Term                | EKS Term                | Description                                                                                     |
|-------------------------|-------------------------|-------------------------------------------------------------------------------------------------|
| Task Definition         | Pod Specification       | Defines the container and volume configuration for a set of containers.                         |
| Task                    | Pod                     | A running set of containers on the cluster.                                                     |
| Service                 | Deployment/StatefulSet  | Manages the desired number of tasks/pods ensuring specified number runs and are updated correctly. |
| Container Instance      | Node                    | An EC2 instance that is part of an ECS Cluster / A Kubernetes worker machine in EKS.            |
| ECS Agent               | Kubelet                 | The agent that runs on each node in the cluster to manage the containers.                       |
| Cluster                 | Cluster                 | A logical set of EC2 instances that host your application containers.                           |
| ECS Service Auto Scaling| Horizontal Pod Autoscaler| Automatically adjusts the number of running tasks/pods based on demand.                        |
| Fargate                 | Fargate                 | A serverless compute engine for containers that works with both ECS and EKS.                    |
| Launch Type             | Node Group              | Determines the type of infrastructure on which your tasks/pods will be launched.                |
| Service Discovery       | Service/Ingress         | Allows your services to discover and talk to each other.                                        |
| Task Role               | Service Account         | Assigns permissions to the task/pod level, controlling what actions they can perform.           |

## For exam

1. A leading social media analytics company is contemplating moving its dockerized application stack into AWS Cloud. The company is not sure about the pricing for using Amazon Elastic Container Service (Amazon ECS) with the EC2 launch type compared to the Amazon Elastic Container Service (Amazon ECS) with the Fargate launch type.

Which of the following is correct regarding the pricing for these two services?


***Answer***With the Fargate launch type, you pay for the amount of vCPU and memory resources that your containerized application requests. vCPU and memory resources are calculated from the time your container images are pulled until the Amazon ECS Task terminates, rounded up to the nearest second. With the EC2 launch type, there is no additional charge for the EC2 launch type. You pay for AWS resources (e.g. EC2 instances or EBS volumes) you create to store and run your application.

```mermaid
graph LR
    A[Pricing Comparison: Amazon ECS EC2 vs Fargate] --> B[Amazon ECS with EC2 Launch Type]
    A --> C[Amazon ECS with Fargate Launch Type]
    A --> D[Choosing Between EC2 and Fargate]
    A --> E[Conclusion]

    B --> F[EC2 Instance Costs]
    B --> G[Control Over Instances]
    B --> H[Additional Costs]
    B --> I[No Extra Charge for ECS]

    F --> J[Depends on Instance Type, Size, Region]
    G --> K[More Control for Optimization]
    H --> L[Costs for ELB, EBS, Data Transfer]

    C --> M[Fargate Pricing]
    C --> N[Simplicity and Ease of Use]
    C --> O[Predictable Pricing]
    C --> P[Potential for Higher Costs]

    M --> Q[Pay for vCPU and Memory Used]
    N --> R[No Server or Cluster Management]
    O --> S[Billed Per-Second, Minimum One Minute]
    P --> T[Can Be More Expensive for Steady Usage]

    D --> U[Resource Optimization vs Simplicity]
    D --> V[Use Case Specific]

    U --> W[Control with EC2 vs Simplicity with Fargate]
    V --> X[EC2 for Steady Usage, Fargate for Variable Needs]

    E --> Y[Depends on Needs and Preferences]
    Y --> Z[EC2 for Control and Cost, Fargate for Ease and Scaling]

```