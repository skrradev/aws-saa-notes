# Active Directory

```mermaid
graph LR
    AD[Active Directory] -->|Manages| DB[Database of Objects]
    AD -->|Installed on| WS[Windows Server with AD Domain Services]
    AD -->|Provides| CSM[Centralized Security Management]
    AD -->|Organizational Structure| OS[Objects: Trees, Domains, Forests]
    AD -->|Domain Controller| DC[Authenticates Users & Manages Domain]
    CSM -->|Tasks| AM[Account Management]
    CSM -->|Tasks| PE[Password Enforcement]
    CSM -->|Tasks| DS[Directory Searches]
    OS -->|Includes| UA[User Accounts]
    OS -->|Includes| CA[Computer Accounts]
    OS -->|Includes| SG[Security Groups]
    AM -->|User Login| UL[User Authentication & Resource Access]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:1px;
    class AD,DB,WS,CSM,OS,DC,AM,PE,DS,UA,CA,SG,UL defaultStyle;



```

```mermaid
graph LR
    subgraph AWS Directory Services
    ManagedAD[AWS Managed Microsoft AD] -->|Trust Relationship| OnPremAD[On-Premise AD]
    ManagedAD -->|Manage Users & Supports MFA| AWSResources[AWS Resources]
    ADConnector[AD Connector] -->|Proxy to On-Premise AD| OnPremAD
    ADConnector -->|Supports MFA| AWSResources
    SimpleAD[Simple AD] -->|AD-Compatible Features| AWSResources
    end

    OnPremAD -->|Integration & Authentication| ManagedAD
    OnPremAD -->|Authentication Only| ADConnector
    AWSResources -.->|Simple AD Functionality| SimpleAD

    classDef aws fill:#ff9900,stroke:#333,stroke-width:2px;
    classDef onprem fill:#36f,stroke:#333,stroke-width:2px;
    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:1px;
    class ManagedAD,ADConnector,SimpleAD aws;
    class OnPremAD onprem;
    class AWSResources defaultStyle;

```

| Feature                   | AWS Managed Microsoft AD | AD Connector | Simple AD |
|---------------------------|--------------------------|--------------|-----------|
| Standalone AD in AWS      | Yes                      | No           | Yes       |
| Manage users locally      | Yes                      | No           | Yes       |
| Supports MFA              | Yes                      | Yes          | No        |
| Trust relationships       | Yes                      | No           | No        |
| Integration with on-prem AD| Yes                      | Yes          | No        |
| Authentication redirection| No                       | Yes          | No        |
| User management           | In AWS                   | On-prem AD   | In AWS    |
| Suitable for              | Larger workloads         | Auth proxy   | Smaller workloads |
| AD feature set            | Full                     | Limited      | Basic     |


```mermaid
graph LR
    IAMIdentityCenter[AWS IAM Identity Center] -->|Direct Integration| ManagedAD[AWS Managed Microsoft AD]
    IAMIdentityCenter -->|AD Connector Proxy| ADC[AD Connector]
    ADC -->|Two-Way Trust| SelfManagedAD[Self-Managed AD On-Premises]

    subgraph AWS Cloud
    ManagedAD
    ADC
    end

    subgraph On-Premises
    SelfManagedAD
    end

    classDef aws fill:#ff9900,stroke:#333,stroke-width:2px;
    classDef onprem fill:#36f,stroke:#333,stroke-width:2px;
    classDef identityCenter fill:#f96,stroke:#333,stroke-width:2px;
    class ManagedAD,ADC aws;
    class SelfManagedAD onprem;
    class IAMIdentityCenter identityCenter;

```
