# EFS Storage Tiers


```mermaid
graph LR;
    EFS_Storage_Tiers[("AWS EFS Storage Tiers")]
    EFS_Storage_Tiers --> Standard[("EFS Standard\n- Default tier\n- Higher cost\n- For frequently accessed files \n-")]
    EFS_Storage_Tiers --> IA[("EFS Infrequent Access (IA)\n- Lower cost\n- For files accessed less frequently\n- Requires Lifecycle Management policy \n-")]

    Standard --> Performance_Standard[("Performance\n- Lower latency\n- Higher throughput \n-")]
    Standard --> Cost_Standard[("Cost\n- Higher than IA\n- No retrieval fee \n-")]

    IA --> Performance_IA[("Performance\n- Slightly higher latency\n- Adequate for infrequent access \n-")]
    IA --> Cost_IA[("Cost\n- Lower storage price\n- Retrieval fee for access \n-")]

    EFS_Storage_Tiers --> Lifecycle_Management[("Lifecycle Management\n- Automates moving files to IA\n- Based on access patterns \n-")]
    Lifecycle_Management --> Policy[("Policy\n- Configure after 7, 14, 30, 60, or 90 days \n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:4px;
    class EFS_Storage_Tiers,Standard,IA,Lifecycle_Management important;




```



## For exam

1. The sourcing team at the US headquarters of a global e-commerce company is preparing a spreadsheet of the new product catalog. The spreadsheet is saved on an Amazon Elastic File System (Amazon EFS) created in us-east-1 region. The sourcing team counterparts from other AWS regions such as Asia Pacific and Europe also want to collaborate on this spreadsheet.

As a solutions architect, what is your recommendation to enable this collaboration with the LEAST amount of operational overhead?


***Answer:*** The spreadsheet on the Amazon Elastic File System (Amazon EFS) can be accessed in other AWS regions by using an inter-region VPC peering connection

Amazon Elastic File System (Amazon EFS) provides a simple, scalable, fully managed elastic NFS file system for use with AWS Cloud services and on-premises resources.

Amazon EFS is a regional service storing data within and across multiple Availability Zones (AZs) for high availability and durability. Amazon EC2 instances can access your file system across AZs, regions, and VPCs, while on-premises servers can access using AWS Direct Connect or AWS VPN.

You can connect to Amazon EFS file systems from EC2 instances in other AWS regions using an inter-region VPC peering connection, and from on-premises servers using an AWS VPN connection. So this is the correct option.


```mermaid
graph LR
    A[VPC Peering Connection in AWS] --> B[Key Features of VPC Peering]
    A --> C[Use Cases for VPC Peering]
    A --> D[Operational Aspects]
    A --> E[Limitations]
    A --> F[Conclusion]

    B --> G[Private Networking]
    B --> H[Inter-Region Connectivity]
    B --> I[No Single Point of Failure]
    B --> J[Bandwidth]

    C --> K[Resource Sharing]
    C --> L[Multi-account Strategies]
    C --> M[Cross-Region Communication]

    D --> N[Routing]
    D --> O[Security Groups and NACLs]
    D --> P[DNS Resolution]
    D --> Q[Transitive Peering]

    E --> R[Overlapping CIDR Blocks]
    E --> S[Transitive Routing]
    E --> T[Scaling and Management]

    F --> U[Powerful Tool for Private Communications]
    F --> V[Useful for Multi-account Setups and Resource Sharing]
    F --> W[Requires Careful Planning in Network Architecture]

```