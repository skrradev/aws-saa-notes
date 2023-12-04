# Snow Family


## Snowball Edge
```mermaid
graph LR
    A[Snowball Edge for Data Transfers] --> B[Physical Data Transport Solution]
    B --> C[Move TB or PB of Data]
    C --> D[Beneficial for Large Data Sets]

    A --> E[Alternative to Network Data Transfer]
    E --> F[Avoids Network Congestion]
    F --> G[Reduces Costs]

    A --> H[Pay per Data Transfer Job]
    H --> I[Priced per Job]

    A --> J[Storage Capabilities]
    J --> K[Block and S3-compatible Object Storage]
    K --> L[Snowball Edge Storage Optimized: 80TB]
    K --> M[Snowball Edge Compute Optimized: 42TB with Computing Capabilities]

    A --> N[Use Cases]
    N --> O[Cloud Migrations, Data Center Decommissioning]
    N --> P[Disaster Recovery]

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
    style H fill:#ccf,stroke:#333,stroke-width:2px
    style J fill:#ccf,stroke:#333,stroke-width:2px
    style N fill:#ccf,stroke:#333,stroke-width:2px

```

## AWS Snowcone
```mermaid
graph LR
A[AWS Snowcone] --> B[Small, Portable Computing]
B --> C[Lightweight and Rugged]
C --> D[Suitable for Harsh Conditions]

    A --> E[Weight]
    E --> F[4.5 Pounds 2.1 kg]

    A --> G[Edge Computing, Storage, and Data Transfer]
    G --> H[Computing and Storage Device]
    H --> I[Transfer Data to and from AWS]

    A --> J[Storage Capacity]
    J --> K[8 TBs of Usable Storage]

    A --> L[Ideal for Space-Constrained Environments]
    L --> M[Compact Size for Limited Spaces]

    A --> N[Accessories]
    N --> O[Own Battery and Cables Required]
    O --> P[Standalone Mode Possible]

    A --> Q[Data Transfer Options]
    Q --> R[Send Back to AWS Offline or Use AWS DataSync]

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style G fill:#ccf,stroke:#333,stroke-width:2px
    style J fill:#ccf,stroke:#333,stroke-width:2px
    style L fill:#ccf,stroke:#333,stroke-width:2px
    style N fill:#ccf,stroke:#333,stroke-width:2px
    style Q fill:#ccf,stroke:#333,stroke-width:2px

```

## AWS Snowmobile
```mermaid
graph LR
A[AWS Snowmobile] --> B[Transfer Exabytes of Data]
B --> C[Designed for Massive Data Movement]
C --> D[1 Exabyte = 1,000 PB = 1,000,000 TBs]

    A --> E[Capacity]
    E --> F[100 Petabytes per Unit]
    F --> G[Use Multiple Units in Parallel]

    A --> H[High Security]
    H --> I[Temperature-Controlled Environments]
    H --> J[GPS Tracking and 24/7 Video Surveillance]

    A --> K[Comparison with Snowball]
    K --> L[Better for Transfers Greater Than 10 PB]
    L --> M[Due to Larger Capacity]

    A --> N[Use Cases]
    N --> O[Data Center Migrations, Disaster Recovery]
    N --> P[When Network Transfer is Not Feasible]

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
    style H fill:#ccf,stroke:#333,stroke-width:2px
    style K fill:#ccf,stroke:#333,stroke-width:2px
    style N fill:#ccf,stroke:#333,stroke-width:2px

```


| Feature | Snowball | Snowcone | Snowmobile |
|---------|----------|----------|------------|
| **Size and Portability** | Portable, but larger and heavier than Snowcone. | Small, light, and highly portable. | Massive, requires a 45-foot long shipping container and a truck for transportation. |
| **Data Capacity** | 50 TB or 80 TB options. | 8 TB of usable storage. | 100 PB per unit. |
| **Primary Use Case** | Data transfer for TBs of data, edge computing. | Edge computing, storage, data transfer in space-constrained environments. | Transferring extremely large datasets, such as exabytes of data. |
| **Data Transfer Method** | Physically shipped to and from AWS. | Physically shipped or can transfer data online using AWS DataSync. | Physically shipped on a truck. |
| **Computing Capabilities** | Compute-optimized and storage-optimized options available. | Limited computing capabilities. | Primarily for data transfer, no computing capabilities. |
| **Security** | AES-256 encryption, GPS tracking, and secure erasure. | Similar to Snowball with encryption and secure data erasure. | High security with temperature-controlled environment, GPS tracking, and 24/7 video surveillance. |
| **Ideal for** | Medium to large-scale data transfer and situations needing local compute power. | Use in remote, space-constrained environments, and for less data-intensive tasks. | Very large-scale data transfers like data center migrations or disaster recovery. |


## AWS Request Snowball Devices from AWS Console
```mermaid
graph TD
A[Request Snowball Devices from AWS Console] --> B[Install Snowball Client/AWS OpsHub on Servers]
B --> C[Connect Snowball to Servers and Copy Files]
C --> D[Ship Back the Device to AWS]
D --> E[Data Loaded into an S3 Bucket]
E --> F[Snowball is Completely Wiped]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style C fill:#ccf,stroke:#333,stroke-width:2px
    style D fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
```


## What is Edge Computing?
```mermaid
graph LR
A[What is Edge Computing?] --> B[Process Data at the Edge]
B --> C[Local Computing Instead of Data Center Transmission]
C --> D["Edge": Near Data Sources like IoT Devices]

    A --> E[Examples of Edge Locations]
    E --> F[Mobile: Trucks, Vessels]
    E --> G[Remote: Mining Stations, Areas with Limited Internet]

    A --> H[AWS Snow Family for Edge Computing]
    H --> I[Snowball Edge and Snowcone]
    I --> J[Designed for Environments Lacking Internet or Computing Resources]

    A --> K[Use Cases of Edge Computing]
    K --> L[Preprocess Data Before Cloud Transfer]
    K --> M[Machine Learning at the Edge]
    K --> N[Transcoding Media Streams Locally]

    A --> O[Post-processing Options]
    O --> P[Ship Devices Back to AWS]
    P --> Q[Data Transfer to AWS Cloud]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
    style H fill:#ccf,stroke:#333,stroke-width:2px
    style K fill:#ccf,stroke:#333,stroke-width:2px
    style O fill:#ccf,stroke:#333,stroke-width:2px

```

## Snow Family  Edge Computing
```mermaid

graph LR
A[Snow Family  Edge Computing] --> B[Snowcone smaller]
B --> C[2 CPUs and 4 GB Memory]
B --> D[Wired and Wireless Access]
B --> E[USB-C Power or Optional Battery]

    A --> F[Snowball Edge  Compute Optimized]
    F --> G[52 vCPUs and 208 GiB RAM]
    F --> H[Optional GPU Support]
    F --> I[42 TB Usable Storage]

    A --> J[Snowball Edge  Storage Optimized]
    J --> K[40 vCPUs and 80 GiB RAM]
    J --> L[Object Storage Clustering]

    A --> M[EC2 and AWS Lambda Support]
    M --> N[Run EC2 Instances and Lambda Functions]
    M --> O[AWS IoT Greengrass Integration]

    A --> P[Long-term Deployment Options]
    P --> Q[1 and 3 Year Discounted Pricing]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
    style J fill:#ccf,stroke:#333,stroke-width:2px
    style M fill:#ccf,stroke:#333,stroke-width:2px
    style P fill:#ccf,stroke:#333,stroke-width:2px
```

## AWS OpsHub
```mermaid
graph LR
A[AWS OpsHub] --> B[Historical Context]
B --> C[CLI Usage for Snow Family Devices]

    A --> D[Modern Solution: AWS OpsHub]
    D --> E[User-Friendly Interface for Device Management]
    E --> F[Installable on Computer or Laptop]

    A --> G[Capabilities of OpsHub]
    G --> H[Unlocking and Configuring Devices]
    G --> I[Transferring Files with Drag-and-Drop]
    G --> J[Launching and Managing Instances]
    G --> K[Monitoring Device Metrics]
    G --> L[Launching AWS Services]

    A --> M[OpsHub Dashboard]
    M --> N[Manage File Storage and Computing Tasks]
    M --> O[Displays Status of Instances, Tasks, and Resources]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style D fill:#ccf,stroke:#333,stroke-width:2px
    style G fill:#ccf,stroke:#333,stroke-width:2px
    style M fill:#ccf,stroke:#333,stroke-width:2px
```


## Solution Architecture: Snowball into Glacier
```mermaid
graph TD
A[Solution Architecture: Snowball into Glacier] --> B[Snowball to S3]
B --> C[Import Data from Snowball to Amazon S3]
C --> D[Amazon S3 as Scalable Storage Solution]

    A --> E[S3 to Glacier]
    E --> F[Apply S3 Lifecycle Policy]
    F --> G[Automatically Move Data to Amazon Glacier]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
```


