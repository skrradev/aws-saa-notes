# EKS

```mermaid
graph LR
    A[Amazon EKS] -->|Managed Kubernetes Service| B[Kubernetes]
    A -->|Alternative to| C[Amazon ECS]
    A -->|Support for| D[EC2 and Fargate]
    B -->|Automates Deployment, Scaling, Management| E[Containerized Applications]
    C -->|AWS's Container Management Service| F[Different API and Features]
    D -->|EC2: Traditional Instances| G[Provision and Manage Servers]
    D -->|Fargate: Serverless Compute Engine| H[No Server Management]
    A -->|Use Case| I[Migration and Continuity for Kubernetes Users]
    B -->|Cloud-Agnostic| J[Hybrid and Multi-Cloud Strategies]

    classDef heading fill:#f96,stroke:#333,stroke-width:2px;
    classDef kubernetes fill:#ff9999,stroke:#333,stroke-width:2px;
    classDef ecs fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef support fill:#99ccff,stroke:#333,stroke-width:2px;
    classDef applications fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef ec2 fill:#ffffcc,stroke:#333,stroke-width:2px;
    classDef fargate fill:#ccccff,stroke:#333,stroke-width:2px;
    classDef useCase fill:#ccffff,stroke:#333,stroke-width:2px;
    classDef cloudAgnostic fill:#cccccc,stroke:#333,stroke-width:2px;

    class A heading;
    class B kubernetes;
    class C ecs;
    class D support;
    class E applications;
    class F ecs;
    class G ec2;
    class H fargate;
    class I useCase;
    class J cloudAgnostic;



```

```mermaid
graph LR
A[AWS Cloud] -->|Hosts Infrastructure| B[VPC]
B -->|Isolated Networking| C[AZs & Subnets]

    subgraph AZs & Subnets
        D[Public Subnet] -->|ELB & NAT Gateway| F[Internet Traffic]
        E[Private Subnet] -->|EKS Nodes & Pods| G[Internal Services]
    end

    G -->|Auto Scaling Group| H[EKS Nodes]
    H -->|Hosts| I[EKS Pods]

    I -->|Kubernetes Containers| J[Application Workloads]
    B -->|Load Balancing| K[ELB]

    classDef aws fill:#ff9900,stroke:#333,stroke-width:2px;
    classDef networking fill:#99ccff,stroke:#333,stroke-width:2px;
    classDef az fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef eks fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef loadbalancer fill:#ccccff,stroke:#333,stroke-width:2px;

    class A aws;
    class B networking;
    class D,E az;
    class G,H,I eks;
    class K loadbalancer;
```


## Amazon EKS Node Types

```mermaid
graph LR
A[Amazon EKS Node Types] -->|Automated Management| B[Managed Node Groups]
A -->|Manual Management| C[Self-Managed Nodes]
A -->|Serverless| D[AWS Fargate]

    B -->|Part of ASG| E[Auto Scaling Group]
    B -->|Instance Types| F[On-Demand & Spot Instances]

    C -->|User Managed| G[Creation & Registration]
    C -->|EKS Optimized AMI| H[Amazon Machine Images]
    C -->|Instance Types| I[On-Demand & Spot Instances]

    D -->|No Server Management| J[No Provisioning]
    D -->|Pay for Use| K[Resource-Based Pricing]

    classDef eks fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef managed fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef selfManaged fill:#ffccff,stroke:#333,stroke-width:2px;
    classDef fargate fill:#ccffff,stroke:#333,stroke-width:2px;

    class A eks;
    class B,C,D managed;
    class E,F,G,H,I selfManaged;
    class J,K fargate;

```

## Amazon EKS Data Volume Options

```mermaid
graph LR
A[Amazon EKS Data Volume Options] -->|Standard Definition| B[StorageClass Manifest]
A -->|Exposure Interface| C[Container Storage Interface CSI]
A -->|Storage Options| D[Supported Storage]

    D -->|Block Storage| E[Amazon EBS]
    D -->|File Storage| F[Amazon EFS]
    D -->|High-Performance| G[Amazon FSx for Lustre]
    D -->|Enterprise Features| H[Amazon FSx for NetApp ONTAP]

    E -->|Use Case| I[Persistent DBs, File Systems]
    F -->|Use Case| J[Shared File Storage, Scalable]
    G -->|Use Case| K[Compute-Intensive Workloads]
    H -->|Use Case| L[Advanced Data Management]

    classDef eks fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef standard fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef interface fill:#ffccff,stroke:#333,stroke-width:2px;
    classDef storage fill:#ccffff,stroke:#333,stroke-width:2px;
    classDef useCase fill:#f9f9f9,stroke:#333,stroke-width:1px;

    class A eks;
    class B,C standard;
    class D storage;
    class E,F,G,H useCase;
    class I,J,K,L useCase;
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
