# NAT Gateway

```mermaid
graph LR
    A[Features of AWS NAT Gateway] --> B[AWS-Managed NAT Service]
    A --> C[High Bandwidth and High Availability]
    A --> D[Cost Model]
    A --> E[Availability Zone Specific with Elastic IP]
    A --> F[Restrictions on Use]
    A --> G[Internet Gateway Requirement]
    A --> H[Bandwidth Capacity]
    A --> I[No Security Groups]

    B --> J[Facilitates Outbound IPv4 Traffic for Private Instances]
    B --> K[Blocks Unsolicited Inbound Traffic]

    C --> L[Auto Scaling to Bandwidth Demands]
    C --> M[Inherent High Availability in AZ]

    D --> N[Pay-as-you-go: Based on Operation Hours and Data Processed]

    E --> O[Specific to an AZ]
    E --> P[Assigned an Elastic IP Address]

    F --> Q[Not for Instances in the Same Subnet]
    F --> R[For Instances in Other Subnets]

    G --> S[Requires an Internet Gateway in VPC]

    H --> T[Baseline 5 Gbps, Scales up to 45 Gbps]

    I --> U[No Virtual Firewall Management Needed]
    U --> V[Internal Security Management by AWS]

    A --> W[Scalable Internet Traffic Solution for VPCs]
    W --> X[Directs Traffic Without Exposing Private Subnets to Internet]
    X --> Y[Eliminates Manual Setup and Maintenance]


```

```mermaid
graph LR
    A[High Availability Setup for AWS NAT Gateway] --> B[Resilience in a Single AZ]
    A --> C[Multiple NAT Gateways for Fault Tolerance]
    A --> D[No Cross-AZ Failover Required]
    A --> E[Diagram Explanation]

    B --> F[Highly Available Within Designated AZ]
    B --> G[Handles Failures Without Service Disruption]

    C --> H[Create NAT Gateways in Multiple AZs]
    C --> I[Continued Service Despite AZ Outage]

    D --> J[Resources in Downed AZ Also Unavailable]
    D --> K[No Internet Access Needed for Downed AZ]

    E --> L[VPC Spans Multiple AZs]
    E --> M[Public and Private Subnets in Each AZ]
    E --> N[Independent Internet Access for Each AZ]

    A --> O[Enhances Network Infrastructure Resilience]
    O --> P[Reduces Single Points of Failure]
    P --> Q[Independent Operation of Instances in Different AZs]

```

| Feature              | NAT Gateway                      | NAT Instance                        |
|----------------------|----------------------------------|-------------------------------------|
| Availability         | Highly available within AZ       | Script managed failover             |
|                      | (create in another AZ for HA)    | between instances                   |
| Bandwidth            | Up to 45 Gbps                    | Depends on EC2 instance type        |
| Maintenance          | Managed by AWS                   | Managed by you (e.g., software,     |
|                      |                                  | OS patches, etc.)                   |
| Cost                 | Per hour & amount of data        | Per hour, EC2 instance type and     |
|                      | transferred                      | size, + network costs               |
| Public IPv4          | Yes                              | Yes                                 |
| Private IPv4         | Yes                              | Yes                                 |
| Security Groups      | No                               | Yes                                 |
| Use as Bastion Host? | No                               | Yes                                 |


