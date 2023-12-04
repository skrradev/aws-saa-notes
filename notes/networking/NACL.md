# NACL

```mermaid
graph LR
    A[NACLs in AWS VPC] --> B[Firewall-Like Function for Subnets]
    A --> C[Association with Subnets]
    A --> D[Rule Evaluation Based on Number]
    A --> E[Typical Last Rule: Deny All]
    A --> F[Rule Numbering Recommendation]
    A --> G[Default Behavior of New NACLs]

    B --> H[Control Traffic To and From Subnets]

    C --> I[Default NACL for New Subnets]

    D --> J[Lower Number = Higher Precedence]
    D --> K[Example: ALLOW vs DENY with Different Numbers]

    E --> L[`*` Rule Denies if No Match]

    F --> M[Increment by 100 for New Rules]

    G --> N[Deny All Traffic Initially]
    N --> O[Requires Adding Rules to Allow Traffic]

    A --> P[Useful for Blocking Specific IPs at Subnet Level]


```

```mermaid
graph LR
    A[Default NACL for AWS VPC] --> B[Allows All IPv4 Traffic by Default]
    A --> C[Inbound Rules]
    A --> D[Outbound Rules]
    A --> E[Custom NACL Recommendation]

    B --> F[Inbound and Outbound Open]

    C --> G[Rule 100: Allow All Types from Any Source 0.0.0.0/0]
    C --> H[Rule *: Deny All if No Match]

    D --> I[Rule 100: Allow All Types to Any Destination]
    D --> J[Rule *: Deny All if No Other Rule Applies]

    E --> K[Advise Against Modifying Default NACL]
    E --> L[Create Custom NACLs for Specific Requirements]

    A --> M[Ensures Initial Connectivity]
    M --> N[Custom NACLs for Enhanced Security and Traffic Control]

```

```mermaid
graph LR
    A[NACLs with Ephemeral Ports in AWS VPC] --> B[Web Tier]
    A --> C[Database Tier]
    A --> D[Database Instance]
    A --> E[Client Ephemeral Port]

    B --> F[Public Subnet: Web NACL]
    F --> G[Outbound TCP on Port 3306 to DB Subnet]
    F --> H[Inbound TCP on Ephemeral Ports 1024-65535 from DB Subnet]

    C --> I[Private Subnet: DB NACL]
    I --> J[Inbound TCP on Port 3306 from Web Subnet]
    I --> K[Outbound TCP on Ephemeral Ports 1024-65535 to Web Subnet]

    D --> L[DB Listening on Port 3306]
    L --> M[MySQL Standard Port]
    L --> N[Located in Private Subnet]

    E --> O[Dynamic Port for Outbound Connection]
    O --> P[Used by Web Tier Clients]

    A --> Q[Stateful Filtering for Return Traffic]
    Q --> R[Critical for Security in Stateless NACLs]

```


# Security Group vs NACL Comparison

| Feature           | Security Group          | NACL                      |
|-------------------|-------------------------|---------------------------|
| Level of Operation| Instance level          | Subnet level              |
| Rule Support      | Allow rules only        | Allow and Deny rules      |
| State             | Stateful                | Stateless                 |
| Traffic Evaluation| All rules evaluated before decision | Rules evaluated in order, first match wins |
| Assignment        | Applies when specified by user | Automatically applies to all instances in subnet |

*Note: This table is created based on the details provided and should be verified with AWS documentation for accuracy.*
