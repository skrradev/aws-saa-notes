# Shield

```mermaid
graph LR
    A[AWS Shield: Managed DDoS Protection Service] --> B[DDoS Attacks]
    A --> C[AWS Shield Standard]
    A --> D[AWS Shield Advanced]

    B --> E[Overwhelm Online Services with Traffic]

    C --> F[Free Service for AWS Customers]
    C --> G[Protection Against Common Network Attacks]
    G --> H[SYN/UDP Floods, Reflection Attacks]

    D --> I[Enhanced Protection for Sophisticated Attacks]
    D --> J[Priced at $3,000 per Month]
    D --> K[For AWS Services like EC2, ELB, CloudFront, Global Accelerator, Route 53]

    K --> L[Additional Protection Benefits]
    L --> M[Access to AWS DDoS Response Team]
    L --> N[Protection Against Usage Fee Spikes]
    L --> O[Automatic Layer 7 Mitigation with AWS WAF]

    A --> P[Designed for Higher Level of DDoS Protection]
    P --> Q[Safeguards and Cost Protection for Businesses]



```


## For exam:
1. A financial services company recently launched an initiative to improve the security of its AWS resources and it had enabled AWS Shield Advanced across multiple AWS accounts owned by the company. Upon analysis, the company has found that the costs incurred are much higher than expected.

Which of the following would you attribute as the underlying reason for the unexpectedly high costs for AWS Shield Advanced service?

***Answer:*** Consolidated billing has not been enabled. All the AWS accounts should fall under a single consolidated billing for the monthly fee to be charged only once

If your organization has multiple AWS accounts, then you can subscribe multiple AWS Accounts to AWS Shield Advanced by individually enabling it on each account using the AWS Management Console or API. You will pay the monthly fee once as long as the AWS accounts are all under a single consolidated billing, and you own all the AWS accounts and resources in those accounts.


```mermaid
graph LR
    A[High Costs of AWS Shield Advanced] --> B[Multiple AWS Accounts Enabled with AWS Shield Advanced]
    A --> C[Consolidated Billing Not Enabled]

    B --> D[Individual Shield Advanced Activation on Each Account]
    B --> E[Monthly Fee for Each Account]

    C --> F[Single Monthly Fee Under Consolidated Billing]
    C --> G[Ownership of All Accounts and Resources Required]

    A --> H[Cost Analysis for Financial Services Company]
    H --> I[Identify Reason for High Service Costs]
    I --> J[Recommendation for Cost Reduction]

    A --> K[Solution: Consolidate Billing for All Accounts]
    K --> L[Charge Monthly Fee Once for All Accounts]

```