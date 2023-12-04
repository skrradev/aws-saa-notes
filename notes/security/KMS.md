# KMS

```mermaid
graph LR
    AWSServices(AWS Services)
    AWSServices -->|Integrated with| KMS[AWS Key Management Service]
    KMS --> IAMIntegration[IAM Integration]
    KMS --> CentralizedControlPanel[Centralized Control Panel]
    KMS --> Auditable[Auditable]
    KMS --> SecureStorage[Use Secure Storage Solutions]
    KMS --> API[API Accessibility]

    IAMIntegration -->|Define Policies| KeyControl[Control Access to Keys]
    CentralizedControlPanel --> ManageKeys[Manage Keys]
    Auditable --> CloudTrailIntegration[AWS CloudTrail Integration]
    SecureStorage --> SecretsManager[AWS Secrets Manager]
    SecureStorage --> EnvVariables[Environment Variables]
    API --> SDKCLI[SDK & CLI]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef awsService fill:#ff9900,stroke:#333,stroke-width:2px;

```


```mermaid
graph LR
    KMS[AWS Key Management Service] --> SymmetricKeys[Symmetric Keys AES-256]
    KMS --> AsymmetricKeys[Asymmetric Keys RSA & ECC]

    SymmetricKeys --> SingleKey[Uses a Single Key for Encryption & Decryption]
    SymmetricKeys --> AWSIntegrated[Used by AWS Services]
    SymmetricKeys --> KMSAPIInteraction[Interact through KMS API]

    AsymmetricKeys --> PublicKey[Public Key for Encryption]
    AsymmetricKeys --> PrivateKey[Private Key for Decryption]
    AsymmetricKeys --> DigitalSignatures[Digital Signatures Operations]
    AsymmetricKeys --> ExternalEncryption[Use Case: Encryption Outside of AWS]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef kms fill:#ff9900,stroke:#333,stroke-width:2px;

```

```mermaid
graph LR
    KMS[AWS Key Management Service] --> AWSManaged[AWS Managed Keys]
    KMS --> CMK[Customer Managed Keys CMKs]
    KMS --> CMKImported[Customer Managed Keys - Imported]

    AWSManaged --> Free[Cost: Free]
    AWSManaged --> AutoRotate3Y[Automatic Rotation: Every 3 Years]

    CMK --> MonthlyCost[Cost: $1/Month]
    CMK --> AutoRotate1Y[Automatic Rotation: Annually Optional]

    CMKImported --> ImportCost[Cost: $1/Month]
    CMKImported --> ManualRotation[Rotation: Manual]

    KMS --> APICosts[KMS API Calls Cost]
    APICosts --> CostPerCall[Cost: $0.03 per 10,000 Calls]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef kms fill:#ff9900,stroke:#333,stroke-width:2px;

```


```mermaid
graph TD
    subgraph OriginalRegion[Original Region eu-west-2]
        EBSVolume[EBS Volume]
        KMSKeyA[KMS Key A]
        Snapshot[Encrypted Snapshot]
        EBSVolume -->|Encrypted with| KMSKeyA
        KMSKeyA --> Snapshot
    end

    subgraph TargetRegion[Target Region ap-southeast-2]
        ReEncryptedSnapshot[Re-encrypted Snapshot]
        KMSKeyB[KMS Key B]
        NewEBSVolume[New EBS Volume]
        ReEncryptedSnapshot -->|Encrypted with| KMSKeyB
        KMSKeyB --> NewEBSVolume
    end

    Snapshot -->|Copied & Re-encrypted| ReEncryptedSnapshot

    classDef region fill:#ddf,stroke:#333,stroke-width:2px;
    classDef kms fill:#f96,stroke:#333,stroke-width:4px;

```

```mermaid
graph TD
    KMSKey[KMS Key]
    DefaultKeyPolicy[Default KMS Key Policy]
    CustomKeyPolicy[Custom KMS Key Policy]
    RootUser[Root User Full Access]
    SpecificUsersAndRoles[Specific Users & Roles]
    AdministerKey[Administer Key]
    UseKey[Use Key]

    KMSKey --> DefaultKeyPolicy
    DefaultKeyPolicy --> RootUser

    KMSKey --> CustomKeyPolicy
    CustomKeyPolicy --> SpecificUsersAndRoles
    SpecificUsersAndRoles --> AdministerKey
    SpecificUsersAndRoles --> UseKey

    classDef key fill:#f96,stroke:#333,stroke-width:2px;
    classDef policy fill:#ddf,stroke:#333,stroke-width:2px;
    classDef users fill:#bdf,stroke:#333,stroke-width:2px;
    class KMSKey key;

```

```mermaid
graph TD
    KMSKey[KMS Key]
    DefaultKeyPolicy[Default KMS Key Policy]
    CustomKeyPolicy[Custom KMS Key Policy]
    RootUser[Root User Full Access]
    SpecificUsersAndRoles[Specific Users & Roles]
    AdministerKey[Administer Key]
    UseKey[Use Key]

    KMSKey --> DefaultKeyPolicy
    DefaultKeyPolicy --> RootUser

    KMSKey --> CustomKeyPolicy
    CustomKeyPolicy --> SpecificUsersAndRoles
    SpecificUsersAndRoles --> AdministerKey
    SpecificUsersAndRoles --> UseKey

    classDef key fill:#f96,stroke:#333,stroke-width:2px;
    classDef policy fill:#ddf,stroke:#333,stroke-width:2px;
    classDef users fill:#bdf,stroke:#333,stroke-width:2px;
    class KMSKey key;

```

```mermaid
graph TD
    CreateSnapshot[1. Create Snapshot Encrypted with CMK]
    AttachKMSKeyPolicy[2. Attach KMS Key Policy Authorize Cross-Account Access]
    ShareEncryptedSnapshot[3. Share Encrypted Snapshot]
    CreateCopyInTargetAccount[4. Create Snapshot Copy in Target Account Encrypted with Target Account's CMK]
    CreateVolume[5. Create Volume from Copied Snapshot]

    CreateSnapshot --> AttachKMSKeyPolicy
    AttachKMSKeyPolicy --> ShareEncryptedSnapshot
    ShareEncryptedSnapshot --> CreateCopyInTargetAccount
    CreateCopyInTargetAccount --> CreateVolume

    classDef step fill:#f9f,stroke:#333,stroke-width:2px;
    class CreateSnapshot,AttachKMSKeyPolicy,ShareEncryptedSnapshot,CreateCopyInTargetAccount,CreateVolume step;

```

```mermaid
graph LR
    MultiRegionKey[Multi-Region Primary Key us-east-1]
    ReplicaKey1[Multi-Region Replica Key us-west-2]
    ReplicaKey2[Multi-Region Replica Key eu-west-1]
    ReplicaKey3[Multi-Region Replica Key ap-southeast-2]
    Sync[Key Synchronization]

    MultiRegionKey -->|Replicated to| ReplicaKey1
    MultiRegionKey -->|Replicated to| ReplicaKey2
    MultiRegionKey -->|Replicated to| ReplicaKey3
    MultiRegionKey -->|Synchronization| Sync

    classDef primary fill:#f96,stroke:#333,stroke-width:2px;
    classDef replica fill:#9cf,stroke:#333,stroke-width:2px;
    class Sync primary;
    class MultiRegionKey,ReplicaKey1,ReplicaKey2,ReplicaKey3 replica;

```

```mermaid
graph LR
    A[AWS KMS Multi-Region Key] -->|Identical Key Across Regions| B[Same Key ID and Material]
    B -->|Automatic Rotation Enabled| C[Key Rotation]
    B -->|Independent Management in Each Region| D[Regional Independence]
    A -->|Global Client-Side Encryption| E[Use Case: Global Data Presence]
    E -->|Example: Global DynamoDB & Aurora| F[Global Encryption/Decryption]
    
    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    class A,B,C,D,E,F default;

```

```mermaid
graph TD
    A[Client-Side Encryption] -->|Encrypt Data Attributes| B[Amazon DynamoDB Encryption Client]
    B -->|Data Sent to DynamoDB| C[DynamoDB Global Tables]
    C -->|Automatic Replication Across Regions| D[Multi-Region Data Availability]
    D -->|Use Multi-Region KMS Keys| E[Decryption in Any Region]
    E -->|Low-Latency Local Access| F[Encrypted Data Access]
    E -->|Security: Encrypted During Transit and at Rest| G[Secure Data Storage]
    G -->|Access Control: Decryption Only by Authorized Clients| H[Enhanced Data Security]

classDef default fill:#f9f,stroke:#333,stroke-width:2px;
class A,B,C,D,E,F,G,H default;

```

```mermaid
graph TD
    A[Client-Side Encryption] -->|Encrypt Data with Primary MRK| B[Encrypt Sensitive Data e.g., SSN]
    B -->|Put Data in Amazon Aurora| C[Amazon Aurora Table]
    C -->|Automatic Replication via Aurora Global Tables| D[Data Replication Across Regions]
    D -->|Access Encrypted Data in Other Regions| E[Retrieve Encrypted Column]
    E -->|Decrypt with Replica MRK| F[Decryption in Local Region]
    F -->|Low-Latency Access to Decrypted Data| G[Enhanced Application Performance]
    B -->|Security: Data Encrypted Before Leaving Client| H[Secure Data Transmission]
    G -->|Access Control: Only Authorized Clients Decrypt| I[Controlled Data Access]

classDef default fill:#f9f,stroke:#333,stroke-width:2px;
class A,B,C,D,E,F,G,H,I default;

```


## For exam

1. A US-based healthcare startup is building an interactive diagnostic tool for COVID-19 related assessments. The users would be required to capture their personal health records via this tool. As this is sensitive health information, the backup of the user data must be kept encrypted in Amazon Simple Storage Service (Amazon S3). The startup does not want to provide its own encryption keys but still wants to maintain an audit trail of when an encryption key was used and by whom.

Which of the following is the BEST solution for this use-case?

***Answer*** Use server-side encryption with AWS Key Management Service keys (SSE-KMS) to encrypt the user data on Amazon S3

AWS Key Management Service (AWS KMS) is a service that combines secure, highly available hardware and software to provide a key management system scaled for the cloud. When you use server-side encryption with AWS KMS (SSE-KMS), you can specify a customer-managed CMK that you have already created. SSE-KMS provides you with an audit trail that shows when your CMK was used and by whom. Therefore SSE-KMS is the correct solution for this use-case.

```mermaid
graph TD
    A[Encrypting Health Records in Amazon S3] --> B[Use Server-Side Encryption with AWS KMS Keys SSE-KMS]
    A --> C[Key Management and Audit Requirements]

    B --> D[Secure Storage with Encryption]
    B --> E[Audit Trail for Key Usage]

    D --> F[Specify Customer-Managed CMK]
    E --> G[Track Usage and Access]

    C --> H[No Own Encryption Keys]
    C --> I[Maintain Audit Trail]

    H --> J[Utilize AWS KMS Managed Keys]
    I --> K[Detailed Logging of Key Usage]

    A --> L[Solution for Healthcare Startup]
    L --> M[Compliant with Data Protection Standards]

```


2. A social photo-sharing company uses Amazon Simple Storage Service (Amazon S3) to store the images uploaded by the users. These images are kept encrypted in Amazon S3 by using AWS Key Management Service (AWS KMS) and the company manages its own AWS KMS keys for encryption. A member of the DevOps team accidentally deleted the AWS KMS key a day ago, thereby rendering the user's photo data unrecoverable. You have been contacted by the company to consult them on possible solutions to this crisis.

As a solutions architect, which of the following steps would you recommend to solve this issue?

***Answer:***As the AWS KMS key was deleted a day ago, it must be in the 'pending deletion' status and hence you can just cancel the KMS key deletion and recover the key

AWS Key Management Service (KMS) makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications. AWS KMS is a secure and resilient service that uses hardware security modules that have been validated under FIPS 140-2.

Deleting an AWS KMS key in AWS Key Management Service (AWS KMS) is destructive and potentially dangerous. Therefore, AWS KMS enforces a waiting period. To delete a KMS key in AWS KMS you schedule key deletion. You can set the waiting period from a minimum of 7 days up to a maximum of 30 days. The default waiting period is 30 days. During the waiting period, the KMS key status and key state is Pending deletion. To recover the KMS key, you can cancel key deletion before the waiting period ends. After the waiting period ends you cannot cancel key deletion, and AWS KMS deletes the KMS key.

```mermaid
graph LR
    A[Recovering Deleted AWS KMS Key for S3 Data] --> B[Check KMS Key Status]
    A --> C[Cancel Key Deletion Process]

    B --> D[Key in 'Pending Deletion' Status]
    B --> E[Within Waiting Period]

    C --> F[Recover the Key]
    C --> G[Restore Access to S3 Data]

    D --> H[Deleted a Day Ago, Likely Recoverable]
    E --> I[Waiting Period Default 7-30 Days]

    A --> J[Consultation as Solutions Architect]
    J --> K[Guide Through Key Recovery Process]
    K --> L[Ensure Key Safety in Future Operations]

    A --> M[Prevent Data Loss Crisis]
    M --> N[Quick Action to Recover Key]
    N --> O[Re-enable Data Encryption and Access]

```