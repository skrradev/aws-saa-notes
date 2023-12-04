# IAM Policy Boundaries

```mermaid
graph LR
    A[IAM Permissions Boundaries] --> B[Definition]
    A --> C[Use Cases]
    A --> D[Restriction]
    A --> E[Application]
    A --> F[Management]
    A --> G[Effective Permissions]
    A --> H[Role Chaining]
    A --> I[Auditing]
    A --> J[Cross-Account Access]

    B --> B1[Limit permissions for IAM entity]

    C --> C1[Delegate permission management]
    C --> C2[Set limits for new roles and users]

    D --> D1[Set maximum allowed permissions]
    D --> D2[Do not grant permissions]

    E --> E1[Managed and inline policies]
    E --> E2[Applicable to users and roles]

    F --> F1[Managed by specific IAM actions]

    G --> G1[Intersection of IAM policies and boundary]

    H --> H1[Parent role's boundary doesn't limit child role]

    I --> I1[Ensure controlled permissions escalation]

    J --> J1[Secure cross-account role access]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:1px;
    class A,B,C,D,E,F,G,H,I,J,B1,C1,C2,D1,D2,E1,E2,F1,G1,H1,I1,J1 defaultStyle;



```


## For exam

1. An IT company wants to review its security best-practices after an incident was reported where a new developer on the team was assigned full access to Amazon DynamoDB. The developer accidentally deleted a couple of tables from the production environment while building out a new feature.

Which is the MOST effective way to address this issue so that such incidents do not recur?

***Answer:*** Use permissions boundary to control the maximum permissions employees can grant to the IAM principals

A permissions boundary can be used to control the maximum permissions employees can grant to the IAM principals (that is, users and roles) that they create and manage. As the IAM administrator, you can define one or more permissions boundaries using managed policies and allow your employee to create a principal with this boundary. The employee can then attach a permissions policy to this principal. However, the effective permissions of the principal are the intersection of the permissions boundary and permissions policy. As a result, the new principal cannot exceed the boundary that you defined. Therefore, using the permissions boundary offers the right solution for this use-case.

```mermaid
graph LR
    A[Addressing Security Incident: Inappropriate DynamoDB Access] --> B[Implement Permissions Boundary]
    
    B --> C[Define Permissions Boundary Using Managed Policies]
    B --> D[Control Max Permissions for IAM Principals]
    B --> E[Apply Boundary to New IAM Principals]
    B --> F[Intersection of Boundary and Permissions Policy]

    C --> G[Set by IAM Administrator]
    D --> H[Limit Permissions Employees Can Grant]
    E --> I[Employee Creates Principals within Boundary]
    F --> J[Effective Permissions are Limited]

    A --> K[Prevent Future Incidents]
    K --> L[Restrict Accidental High-Level Access]
    L --> M[Ensure Safe Principal Creation by Employees]

```
