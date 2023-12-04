# AWS DataSync

```mermaid
graph LR
    A[AWS DataSync] --> B[Purpose]
    B --> C[Move Large Amounts of Data to/from AWS]
    C --> D[Transfer from On-Premises or Other Clouds to AWS]

    A --> E[Data Transfer Protocols]
    E --> F[Supports NFS, SMB, HDFS, S3 API]
    F --> G[Requires Agent for On-Premises/Other Clouds]

    A --> H[Synchronization Targets]
    H --> I[Amazon S3: All Storage Classes]
    H --> J[Amazon EFS: Scalable File Storage]
    H --> K[Amazon FSx: Fully Managed File Systems]

    A --> L[Replication Tasks]
    L --> M[Schedule Recurring Tasks]
    M --> N[Hourly, Daily, Weekly]

    A --> O[File Permissions and Metadata]
    O --> P[Preserves During Transfer]
    P --> Q[Maintains POSIX Attributes]

    A --> R[Network Efficiency]
    R --> S[Up to 10 Gbps per Task]
    S --> T[Configurable Bandwidth Limit]

    A --> U[Usage Scenarios]
    U --> V[File Sharing, Public Datasets, Business Application Integration]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
    style H fill:#ccf,stroke:#333,stroke-width:2px
    style L fill:#ccf,stroke:#333,stroke-width:2px
    style O fill:#ccf,stroke:#333,stroke-width:2px
    style R fill:#ccf,stroke:#333,stroke-width:2px
    style U fill:#ccf,stroke:#333,stroke-width:2px



```

# AWS  DataSync - NFS/SMB to AWS

```mermaid
graph LR
A[AWS DataSync - NFS/SMB to AWS] --> B[On-Premises Setup]
B --> C[NFS or SMB Server]
C --> D[DataSync Agent on VM or Physical Server]
D --> E[Option to Use Snowcone for Limited Connectivity]

    A --> F[Data Transfer]
    F --> G[Secured by TLS Encryption]
    G --> H[Managed Transfer with Data Integrity Checks]

    A --> I[AWS Storage Resources]
    I --> J[Amazon S3: Multiple Storage Classes]
    J --> K[Amazon EFS: Elastic NFS File System]
    K --> L[Amazon FSx: Managed Third-Party File Systems]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
    style I fill:#ccf,stroke:#333,stroke-width:2px

```


# AWS DataSync - Transfer between AWS Storage Services

```mermaid
graph LR
A[AWS DataSync - Transfer between AWS Storage Services] --> B[From and To AWS Storage Services]
B --> C[Amazon S3: Object Storage Service]
B --> D[Amazon EFS: Elastic File Storage]
B --> E[Amazon FSx: Managed Third-Party File Systems]

    A --> F[Functionality]
    F --> G[Bi-Directional Data Copy]
    G --> H[Preserves File System Metadata]

    A --> I[Use Case]
    I --> J[Data Migration, Data Protection, Hybrid Cloud Storage]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
    style I fill:#ccf,stroke:#333,stroke-width:2px

```

# AWS DataSync - Transfer between AWS Storage Services

```mermaid
graph LR
A[AWS DataSync - Transfer between AWS Storage Services] --> B[From and To AWS Storage Services]
B --> C[Amazon S3: Object Storage Service]
B --> D[Amazon EFS: Elastic File Storage]
B --> E[Amazon FSx: Managed Third-Party File Systems]

    A --> F[Functionality]
    F --> G[Bi-Directional Data Copy]
    G --> H[Preserves File System Metadata]

    A --> I[Use Case]
    I --> J[Data Migration, Data Protection, Hybrid Cloud Storage]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
    style I fill:#ccf,stroke:#333,stroke-width:2px
```


| Feature                   | AWS Storage Gateway                                    | AWS DataSync                                        |
|---------------------------|--------------------------------------------------------|-----------------------------------------------------|
| **Primary Use Case**      | Hybrid storage service that enables on-premises access to virtually unlimited cloud storage. | High-speed online data transfer service between on-premises storage and AWS services. |
| **Integration**           | Integrates with existing applications via standard storage protocols (NFS, SMB, iSCSI). | Integrates with NFS, SMB, and object storage protocols for data transfer. |
| **Data Transfer**         | Suitable for scenarios where on-premises applications need frequent access to data stored in AWS. | Optimized for moving large volumes of data into and out of AWS rapidly and efficiently. |
| **Performance**           | Depends on the chosen gateway type and local resources. | High-performance data transfers; scales to transfer petabytes of data. |
| **Storage Services**      | Works with Amazon S3, EBS, and Glacier. | Works primarily with Amazon S3, EFS, and FSx for Windows File Server. |
| **Cost**                  | Charges for gateway usage, data storage, and data retrieval costs. | Charges based on the amount of data transferred. |
| **Deployment**            | Deployed as a virtual machine or hardware appliance on-premises. | Deployed as an agent on-premises or in the cloud. |
| **Caching**               | Supports local caching for frequently accessed data. | No local caching; focuses on efficient data transfer. |
| **Backup and Archiving**  | Supports backup and archival solutions, integrating with existing backup applications. | More focused on data transfer than backup/archiving. However, can be used for initial backup transfers. |
| **Data Synchronization**  | Not specifically designed for data synchronization tasks. | Designed for efficient, periodic data synchronization tasks. |
| **Encryption and Security** | Data encrypted in transit and at rest; integrates with AWS IAM for access control. | Data encrypted in transit; integrates with AWS IAM and Key Management Service for encryption and access control. |
