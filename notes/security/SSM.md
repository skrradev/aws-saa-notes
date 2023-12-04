# SSM


```mermaid
graph TD
    A[Start: SSM Parameter Store Usage] --> B[Secure Storage for Config Data and Secrets]

    B --> C[Option to Encrypt Data Using AWS KMS]
    B --> D[Serverless and Scalable Service]
    B --> E[Version Tracking of Stored Data]
    B --> F[Security Management via AWS IAM]

    C --> G[Retrieve Encrypted Configurations]
    G --> H[AWS KMS for Decryption Services]

    D --> I[Retrieve Configurations for Applications]
    F --> J[Integrate with Amazon EventBridge for Notifications]
    E --> K[Integrate with AWS CloudFormation]

    H --> L[End: Configurations Accessed Securely]
    I --> L
    K --> L
    J --> L

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    class A,B,C,D,E,F,G,H,I,J,K,L default;


```

```mermaid
graph TD
    A[SSM Parameter Store] --> B[Parameter Hierarchy]
    B --> C[Dev Environment]
    B --> D[Prod Environment]
    
    C --> E[/my-department/my-app/dev/]
    D --> F[/my-department/my-app/prod/]

    E --> G[Dev Database URL]
    E --> H[Dev Database Password]
    E --> I[Dev Lambda Function Access]
    
    F --> J[Prod Database URL]
    F --> K[Prod Database Password]
    F --> L[Prod Lambda Function Access]
    
    G --> M[Retrieval via GetParameters or GetParametersByPath]
    H --> M
    J --> M
    K --> M

    M --> N[Other Parameters and Secrets Integration]
    N --> O[Integration with AWS Secrets Manager]
    N --> P[Use in Amazon Machine Images for Lambda]
    
    I --> Q[Role-Based Access for Dev]
    L --> R[Role-Based Access for Prod]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    class A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R default;

```

## a table comparing the features of Standard and Advanced parameter tiers in the AWS Systems Manager Parameter Store

| Feature                                         | Standard   | Advanced           |
|-------------------------------------------------|------------|--------------------|
| Total number of parameters allowed (per AWS account and Region) | 10,000     | 100,000            |
| Maximum size of a parameter value               | 4 KB       | 8 KB               |
| Parameter policies available                    | No         | Yes                |
| Cost                                            | No additional charge | Charges apply       |
| Storage Pricing                                 | Free       | $0.05 per advanced parameter per month |


```mermaid
graph LR
    A[AWS Systems Manager Parameter Store] --> B[Secure Storage]
    A --> C[Hierarchical Storage]
    A --> D[Serverless]
    A --> E[Scalable and Durable]
    A --> F[Easy Integration]
    A --> G[Version Tracking]
    A --> H[Notifications]

    B --> I[Uses AWS KMS for Encryption]
    C --> J[Organized in Hierarchy]
    D --> K[Managed Service]
    E --> L[Scales with Needs]
    F --> M[Integrates with AWS Services]
    G --> N[History of Changes]
    H --> O[Amazon EventBridge Notifications]

    P[Parameter Policies for Advanced Parameters] --> Q[Expiration]
    P --> R[ExpirationNotification]
    P --> S[NoChangeNotification]

    Q --> T[Auto-deletes after Specified Time]
    R --> U[Notifies before Expiration]
    S --> V[Notifies if No Change after Period]

    A --> P

```