# WAF

```mermaid
graph LR
    A[AWS WAF] --> B[Layer 7 Protection]
    A --> C[Deployment]
    A --> D[Customizable Rules]
    A --> E[Integration with AWS Monitoring Tools]

    B --> F[Inspect HTTP/HTTPS Traffic]

    C --> G[Application Load Balancer ALB]
C --> H[API Gateway]
C --> I[CloudFront]
C --> J[AppSync GraphQL API]
C --> K[Cognito User Pool]

D --> L[Filter Traffic Based on Conditions]
L --> M[IP Addresses, HTTP Headers, Body, URI Strings]
L --> N[SQL Injection, Cross-site Scripting]

E --> O[Automated Responses to Threats]
E --> P[Real-time Metrics and Logs]
P --> Q[Amazon CloudWatch]

A --> R[Protects Web Applications from Exploits and Bots]



```

```mermaid
graph LR
    A[AWS WAF] --> B[Web ACL Rules]
    A --> C[Regional Deployment]
    A --> D[Rule Groups]

    B --> E[IP Set]
    B --> F[Protection Mechanisms]
    B --> G[Size Constraints]
    B --> H[Geo-Match]
    B --> I[Rate-Based Rules]

    E --> J[Specify up to 10,000 IP Addresses]
    F --> K[Inspect HTTP Headers, Body, URI Strings]
    F --> L[Protect Against SQL Injection, XSS]
    G --> M[Apply Size Constraints on Request Parts]
    H --> N[Block or Allow Traffic Based on Location]
    I --> O[Limit Requests from an IP Address]

    C --> P[Applies to Resources in a Specific Region]
    P --> Q[Except with CloudFront Global]

    D --> R[Collection of Predefined Rules]
    R --> S[Reuse Across Multiple Web Applications]

    A --> T[Protects Web Applications from Common Exploits]

```

```mermaid
graph LR
    A[Configuration: AWS WAF with Global Accelerator and ALB] --> B[WAF and Load Balancers]
    A --> C[AWS Global Accelerator]
    A --> D[Combination for Fixed IP and Protection]
    A --> E[Region Consideration]

    B --> F[AWS WAF Protects Web Applications]
    B --> G[Used with ALB at Layer 7]
    B --> H[Not Compatible with Network Load Balancers]

    C --> I[Provides Fixed IP Addresses]
    C --> J[Improves Global Availability and Performance]
    C --> K[Static IP as Fixed Entry Point]

    D --> L[Direct Traffic to ALB with Fixed IP]
    D --> M[Attach AWS WAF to ALB]
    D --> N[Stable Entry Point and Protection]

    E --> O[WebACL in Same Region as ALB]

    A --> P[Useful for Compliance and Whitelisting]
    P --> Q[Optimal Global Routing to Nearest ALB]

```


## For exam:

1. A media company runs a photo-sharing web application that is accessed across three different countries. The application is deployed on several Amazon Elastic Compute Cloud (Amazon EC2) instances running behind an Application Load Balancer. With new government regulations, the company has been asked to block access from two countries and allow access only from the home country of the company.

Which configuration should be used to meet this changed requirement?


***Answer***: Configure AWS Web Application Firewall (AWS WAF) on the Application Load Balancer in a Amazon Virtual Private Cloud (Amazon VPC)

You can use AWS WAF with your Application Load Balancer to allow or block requests based on the rules in a web access control list (web ACL). Geographic (Geo) Match Conditions in AWS WAF allows you to use AWS WAF to restrict application access based on the geographic location of your viewers. With geo match conditions you can choose the countries from which AWS WAF should allow access.

Geo match conditions are important for many customers. For example, legal and licensing requirements restrict some customers from delivering their applications outside certain countries. These customers can configure a whitelist that allows only viewers in those countries. Other customers need to prevent the downloading of their encrypted software by users in certain countries. These customers can configure a blacklist so that end-users from those countries are blocked from downloading their software.


```mermaid
graph LR
    A[Implement Geographic Restrictions using AWS WAF and ALB] --> B[AWS WAF Configuration]
    A --> C[Associate Web ACL with ALB]

    B --> D[Create Web ACL]
    B --> E[Geo Match Rule]
    B --> F[Set Default Action]
    B --> G[Testing]

    D --> H[Web Access Control List]
    E --> I[Specify Allowed Country's ISO Code]
    F --> J[Block Requests Not From Allowed Country]
    G --> K[Count Matches for Initial Testing]

    C --> L[Attach Web ACL to ALB]
    C --> M[Verify Configuration]

    L --> N[ALB Fronts EC2 Instances]
    M --> O[Check Traffic from Allowed Country]
    M --> P[Ensure Blocking of Two Restricted Countries]

    A --> Q[Compliance with Government Regulations]

```