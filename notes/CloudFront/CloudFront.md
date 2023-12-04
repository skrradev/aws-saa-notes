# CloudFront

```mermaid
graph LR
    A[AWS CloudFront Overview] --> B[Content Delivery Network CDN]
    A --> C[Read Performance Improvement]
    A --> D[User Experience Enhancement]
    A --> E[Global Network of PoPs]
    A --> F[DDoS Protection Integration]

    B --> G[High Availability and Speed]
    C --> H[Caching at Edge Locations]
    C --> I[Reduced Latency]

    D --> J[Proximity to Users]
    D --> K[Quick Content Delivery and Reduced Load Times]

    E --> L[216 Points of Presence Worldwide]
    E --> M[Edge Locations and Regional Edge Caches]

    F --> N[Integrates with AWS Shield]
    F --> O[AWS WAF for Additional Security]

    A --> P[Visual Representation]
    P --> Q[Global Distribution of Network]
    P --> R[Indicates Widespread Nature of Edge Locations]

    A --> S[Source: AWS CloudFront Features Page]

```

```mermaid
graph LR
    A[CloudFront  Origins Overview] --> B[S3 Bucket as Origin]
    A --> C[Custom Origin HTTP]

    B --> D[Distribute and Cache Files at Edge]
    B --> E[Enhanced Security with Origin Access Control]
    B --> F[Origin Access Control Replaces Origin Access Identity]
    B --> G[CloudFront as Ingress for Uploading to S3]

    C --> H[HTTP Endpoints as Origins]
    C --> I[Application Load Balancer as Origin]
    C --> J[EC2 Instance as Origin]
    C --> K[S3 Website as Origin]
    C --> L[Flexibility with Any HTTP Backend as Origin]

    A --> M[Interactions with AWS Services]
    M --> N[Integration with S3, EC2, and Load Balancers]
    N --> O[Configuration Options for Content Delivery and Security]

```


```mermaid
graph LR
    A[CloudFront - S3 as an Origin] --> B[Origin S3 Bucket]
    A --> C[Edge Locations]
    A --> D[Users]
    A --> E[AWS Cloud]
    A --> F[Private AWS]
    A --> G[OAC Origin Access Control]
    A --> H[Origin Access Control + S3 Bucket Policy]

    B --> I[Source of Content Distribution]
    
    C --> J[Los Angeles]
    C --> K[Mumbai]
    C --> L[São Paulo]
    C --> M[Melbourne]
    J --> N[Data Center for Content Caching]
    K --> N
    L --> N
    M --> N

    D --> O[Public www]
    O --> P[End-Users Access via Internet]

    E --> Q[Pathway of Content Distribution]
    F --> R[Amazon's Private Network for Secure Delivery]

    G --> S[Manage Access to S3 Content]
    H --> T[Combined Access Control Measures]

    A --> U[Enhanced Delivery Speed and Security]

```


```mermaid
graph LR
    A[Comparison: CloudFront vs S3 Cross Region Replication] --> B[CloudFront]
    A --> C[S3 Cross Region Replication]

    B --> D[Global Edge Network]
    B --> E[Caches Files for TTL]
    B --> F[Great for Static Content]

    D --> G[Worldwide Edge Locations]
    E --> H[Temporary Storage at Edge Locations]
    F --> I[For Files like Images, CSS, JavaScript]

    C --> J[Setup Required for Each Region]
    C --> K[Files Updated in Near Real-Time]
    C --> L[Replicated Files are Read-Only]
    C --> M[Great for Dynamic Content]

    J --> N[Manual Configuration Needed]
    K --> O[Latest File Version Across Regions]
    L --> P[Ensures Data Consistency]
    M --> Q[For Frequently Changing Files]

    A --> R[Distinct Uses for Different Content Types]
    R --> S[Global Distribution vs Regional Availability]


```


| Feature | CloudFront | S3 Cross Region Replication |
|---------|------------|-----------------------------|
| Network Type | Global Edge network | Inter-region data replication |
| Content Type | Static content | Dynamic content |
| Availability | Global | Specific regions set up by user |
| Cache Duration | TTL (e.g., a day) | N/A (real-time replication) |
| Update Frequency | As per TTL or when invalidated | Near real-time |
| Access Type | Public (usually) | Read-only after replication |
| Best Used For | Content that must be available everywhere | Content that needs low-latency access in select regions |


```mermaid
graph LR
    A[Origin Access Control OAC in Amazon CloudFront] --> B[Supports All Amazon S3 Buckets]
    A --> C[Compatible with S3 Server-Side Encryption]
    A --> D[Allows Dynamic Requests to S3]
    A --> E[Pre-Configuration Requirements]
    A --> F[Settings for Signing Behavior]

    B --> G[Including Post-December 2022 AWS Regions]
    
    C --> H[Works with AWS KMS SSE-KMS]
    
    D --> I[Supports PUT and DELETE Requests]

    E --> J[Set S3 Object Ownership to 'Bucket owner enforced']
    E --> K[Grant CloudFront Service Principal Access via Bucket Policy]

    F --> L[Always Signing Requests Recommended]
    F --> M[Never Signing Requests]
    F --> N[Not Overriding Viewer's Authorization Header]

    A --> O[Ensuring Secure Content Delivery]
    O --> P[Authenticate Requests from CloudFront to S3]

```

```mermaid
graph LR
    A[Configuring Amazon CloudFront with ALB/EC2 as Origin] --> B[Edge Location Public IPs]
    A --> C[ALB Must be Public]
    A --> D[EC2 Instances Must be Public]
    A --> E[Security Group Configuration]

    B --> F[Allow CloudFront IPs in Security Groups]
    F --> G[Accept Incoming Requests from CloudFront]

    C --> H[Publicly Accessible Load Balancer]
    H --> I[Public IP Address and Internet Reachable]

    D --> J[Publicly Accessible EC2 Instances]
    J --> K[Public IP Address and Internet Reachable]

    E --> L[Configure Security Groups]
    L --> M[Allow Traffic from CloudFront Edge Locations]

    A --> N[Link to CloudFront IP Ranges]
    N --> O[Update Security Groups Accordingly]

```

```mermaid
graph LR
    A[CloudFront Geo Restriction Geoblocking] --> B[Allowlist]
    A --> C[Blocklist]
    A --> D[Geo-IP Database]
    A --> E[Use Case]

    B --> F[Access Only for Approved Countries]
    C --> G[Prevent Access from Specified Countries]
    D --> H[Determine Location from IP Address]
    E --> I[Enforce Copyright Laws by Region]

    A --> J[Control Content Access Based on Geographic Location]

```


```mermaid
graph LR
    A[Amazon CloudFront Price Classes] --> B[Price Class All]
    A --> C[Price Class 200]
    A --> D[Price Class 100]

    B --> E[Best Performance]
    B --> F[Uses All Regions]
    B --> G[Most Expensive Option]

    C --> H[Balance Between Cost and Performance]
    C --> I[Includes Most Regions]
    C --> J[Excludes Most Expensive Regions]

    D --> K[Most Cost-Effective]
    D --> L[Uses Least Expensive Regions]
    D --> M[Reduced Performance and Coverage]

    A --> N[Optimize Costs by Limiting Edge Locations]

```

```mermaid
graph LR
    A[CloudFront Cache Invalidations] --> B[Backend Content Update]
    A --> C[Continued Serving of Cached Content]
    A --> D[Cache Invalidation Process]
    A --> E[Invalidation Scope]

    B --> F[Example: S3 Bucket Update]
    C --> G[TTL Expiration for Cached Content]
    
    D --> H[Forces Fetch of Latest Content from Origin]
    D --> I[Immediate Content Refresh]
    
    E --> J[Wildcard '*' for All Files]
    E --> K[Specific Paths like '/images/*']

    A --> L[Diagram Illustration]
    L --> M[Users Request 'index.html']
    L --> N[CloudFront Directs to Edge Locations]
    L --> O[Invalidation Requests Update Cached Content]

```


## For exam

1. Amazon CloudFront offers a multi-tier cache in the form of regional edge caches that improve latency. However, there are certain content types that bypass the regional edge cache, and go directly to the origin.

Which of the following content types skip the regional edge cache? (Select two)

***Answer:*** Dynamic content, as determined at request time (cache-behavior configured to forward all headers)

Amazon CloudFront is a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.

CloudFront points of presence (POPs) (edge locations) make sure that popular content can be served quickly to your viewers. CloudFront also has regional edge caches that bring more of your content closer to your viewers, even when the content is not popular enough to stay at a POP, to help improve performance for that content.

Dynamic content, as determined at request time (cache-behavior configured to forward all headers), does not flow through regional edge caches, but goes directly to the origin. So this option is correct.

Proxy methods PUT/POST/PATCH/OPTIONS/DELETE go directly to the origin

Proxy methods PUT/POST/PATCH/OPTIONS/DELETE go directly to the origin from the POPs and do not proxy through the regional edge caches. So this option is also correct.

```mermaid
graph LR
    A[Amazon CloudFront Content Flow] --> B[Content Types Bypassing Regional Edge Cache]
    A --> C[Content Types Utilizing Regional Edge Cache]

    B --> D[Dynamic Content Configured to Forward All Headers]
    B --> E[Proxy Methods: PUT/POST/PATCH/OPTIONS/DELETE]

    D --> F[Directly to Origin]
    E --> G[Directly to Origin from POPs]

    C --> H[Static and Cached Content]
    C --> I[Content Popular Enough to Stay at POP]

    A --> J[CDN Service for Data and Applications]
    J --> K[Low Latency, High Transfer Speeds]
    K --> L[Improved Performance for Various Content Types]

```