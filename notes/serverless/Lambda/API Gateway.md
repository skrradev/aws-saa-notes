# AWS API Gateway

```mermaid
graph LR
API_Gateway[AWS API Gateway] --> Lambda_Integration[Integration with AWS Lambda]
API_Gateway --> WebSocket_Support[WebSocket Protocol Support]
API_Gateway --> API_Versioning[API Versioning]
API_Gateway --> Environment_Handling[Environment Handling]
API_Gateway --> Security_Features[Security Features]
API_Gateway --> API_Keys_Management[API Keys and Request Throttling]
API_Gateway --> Swagger_OpenAPI_Import[Swagger/OpenAPI Import]
API_Gateway --> Request_Response_Transformation[Request and Response Transformations]
API_Gateway --> SDK_Generation[SDK and API Specification Generation]
API_Gateway --> Caching[Caching of API Responses]

    style API_Gateway fill:#f9f,stroke:#333,stroke-width:2px
    style Lambda_Integration fill:#cff,stroke:#333,stroke-width:2px
    style WebSocket_Support fill:#cff,stroke:#333,stroke-width:2px
    style API_Versioning fill:#cff,stroke:#333,stroke-width:2px
    style Environment_Handling fill:#cff,stroke:#333,stroke-width:2px
    style Security_Features fill:#cff,stroke:#333,stroke-width:2px
    style API_Keys_Management fill:#cff,stroke:#333,stroke-width:2px
    style Swagger_OpenAPI_Import fill:#cff,stroke:#333,stroke-width:2px
    style Request_Response_Transformation fill:#cff,stroke:#333,stroke-width:2px
    style SDK_Generation fill:#cff,stroke:#333,stroke-width:2px
    style Caching fill:#cff,stroke:#333,stroke-width:2px
```
```mermaid
graph LR
API_Gateway[AWS API Gateway] --> Lambda_Function[Lambda Function]
API_Gateway --> HTTP[HTTP Endpoints]
API_Gateway --> AWS_Service[Integration with AWS Service]

    Lambda_Function --> Expose_REST_APIs[Expose REST APIs via Serverless Lambda]
    
    HTTP --> Internal_HTTP_APIs[Internal HTTP APIs On-Premises]
    HTTP --> Application_Load_Balancers[Through Application Load Balancers]
    HTTP --> HTTP_Features[Add Features like Rate Limiting, Caching, Auth, API Keys]

    AWS_Service --> Step_Function[Trigger AWS Step Function]
    AWS_Service --> SQS[Post Message to SQS]
    AWS_Service --> Service_Public_Exposure[Make Services Publicly Available]
    AWS_Service --> Rate_Control[Control Rate of Use]

    style API_Gateway fill:#f9f,stroke:#333,stroke-width:2px
    style Lambda_Function fill:#cff,stroke:#333,stroke-width:2px
    style HTTP fill:#cff,stroke:#333,stroke-width:2px
    style AWS_Service fill:#cff,stroke:#333,stroke-width:2px
    style Expose_REST_APIs fill:#cfc,stroke:#333,stroke-width:2px
    style Internal_HTTP_APIs fill:#cfc,stroke:#333,stroke-width:2px
    style Application_Load_Balancers fill:#cfc,stroke:#333,stroke-width:2px
    style HTTP_Features fill:#cfc,stroke:#333,stroke-width:2px
    style Step_Function fill:#cfc,stroke:#333,stroke-width:2px
    style SQS fill:#cfc,stroke:#333,stroke-width:2px
    style Service_Public_Exposure fill:#cfc,stroke:#333,stroke-width:2px
    style Rate_Control fill:#cfc,stroke:#333,stroke-width:2px
```
## API_Gateway --> Kinesis_Data_Streams
```mermaid
graph TD
Client[Client] --> API_Gateway[API Gateway]
API_Gateway --> Kinesis_Data_Streams[Kinesis Data Streams]
Kinesis_Data_Streams --> Kinesis_Data_Firehose[Kinesis Data Firehose]
Kinesis_Data_Firehose --> Amazon_S3[Amazon S3]

    style Client fill:#f9f,stroke:#333,stroke-width:2px
    style API_Gateway fill:#cff,stroke:#333,stroke-width:2px
    style Kinesis_Data_Streams fill:#cff,stroke:#333,stroke-width:2px
    style Kinesis_Data_Firehose fill:#cff,stroke:#333,stroke-width:2px
    style Amazon_S3 fill:#cff,stroke:#333,stroke-width:2px
```

## API_Gateway --> Endpoints
```mermaid
graph LR
API_Gateway[AWS API Gateway] --> Edge_Optimized[Edge-Optimized Endpoint]
API_Gateway --> Regional[Regional Endpoint]
API_Gateway --> Private[Private Endpoint]

    Edge_Optimized --> Global_Clients[Best for Global Clients]
    Edge_Optimized --> Multiple_Locations[Deployed via CloudFront Edge Locations]
    Edge_Optimized --> Single_Region_Hosted[Hosted in Single AWS Region]

    Regional --> Close_Clients[Best for Local Clients]
    Regional --> Same_Region[Within Same AWS Region]
    Regional --> Manual_CloudFront_Control[Can Combine with CloudFront Manually]

    Private --> VPC_Access[Accessible within Amazon VPC]
    Private --> ENIs[Uses Elastic Network Interfaces]
    Private --> No_Public_Internet[Not Accessible from Public Internet]
    Private --> Controlled_Access[Access Controlled by Resource Policy]

    style API_Gateway fill:#f9f,stroke:#333,stroke-width:2px
    style Edge_Optimized fill:#cff,stroke:#333,stroke-width:2px
    style Regional fill:#cff,stroke:#333,stroke-width:2px
    style Private fill:#cff,stroke:#333,stroke-width:2px
```

| Feature/Endpoint Type | Edge-Optimized            | Regional                   | Private                    |
|-----------------------|---------------------------|----------------------------|----------------------------|
| Accessibility         | Global clients            | Clients within the same AWS region | Clients within a VPC          |
| Latency               | Improved via global edge locations | Potentially lower for regional clients | N/A (isolated to VPC)      |
| Hosting Region        | Single AWS region         | Single AWS region          | Single AWS region          |
| CloudFront            | Automatically integrated  | Can be manually combined   | Not applicable             |
| VPC Access            | Via internet              | Via internet               | Via VPC endpoint (ENI)     |
| Use Case              | General use with global access | Localized use with some control over caching | Strictly controlled internal access |
| Access Control        | Managed via API Gateway   | Managed via API Gateway and optionally CloudFront | Managed via VPC and resource policies |


## API Gateway - Security
```mermaid
graph TD
API_Gateway_Security[API Gateway - Security] --> User_Authentication[User Authentication]
API_Gateway_Security --> HTTPS_Security[Custom Domain Name HTTPS Security]

    User_Authentication --> IAM_Roles[IAM Roles]
    User_Authentication --> Cognito[Cognito]
    User_Authentication --> Custom_Authorizer[Custom Authorizer]

    HTTPS_Security --> ACM_Integration[Integration with AWS Certificate Manager]
    HTTPS_Security --> Endpoint_Settings[Endpoint SSL Certificate Settings]
    HTTPS_Security --> DNS_Configuration[DNS Configuration]

    ACM_Integration --> Edge_Optimized_SSL[Edge-Optimized: SSL in us-east-1]
    ACM_Integration --> Regional_SSL[Regional: SSL in Same Region]

    DNS_Configuration --> CNAME_Setup[CNAME or A-alias in Route 53]

    style API_Gateway_Security fill:#f9f,stroke:#333,stroke-width:2px
    style User_Authentication fill:#cff,stroke:#333,stroke-width:2px
    style HTTPS_Security fill:#cff,stroke:#333,stroke-width:2px
    style IAM_Roles fill:#cfc,stroke:#333,stroke-width:2px
    style Cognito fill:#cfc,stroke:#333,stroke-width:2px
    style Custom_Authorizer fill:#cfc,stroke:#333,stroke-width:2px
    style ACM_Integration fill:#cfc,stroke:#333,stroke-width:2px
    style Endpoint_Settings fill:#cfc,stroke:#333,stroke-width:2px
    style DNS_Configuration fill:#cfc,stroke:#333,stroke-width:2px
    style Edge_Optimized_SSL fill:#cfc,stroke:#333,stroke-width:2px
    style Regional_SSL fill:#cfc,stroke:#333,stroke-width:2px
    style CNAME_Setup fill:#cfc,stroke:#333,stroke-width:2px
```


# AWS API Gateway vs AWS Application Load Balancer (ALB) Comparison

| Feature | AWS API Gateway | AWS Application Load Balancer (ALB) |
|---------|-----------------|-------------------------------------|
| **Purpose** | Manages API calls with features like traffic management, authorization, monitoring, and API version management. | Distributes incoming application traffic across multiple targets in multiple Availability Zones. |
| **Protocol Support** | HTTP/HTTPS, WebSocket, RESTful APIs. | HTTP/HTTPS, WebSocket. |
| **Routing** | API path and method-based routing. | Content type, host, path, HTTP headers, methods, query parameters, source IP-based routing. |
| **Integration** | Direct integration with AWS services like Lambda and DynamoDB. | Targets EC2 instances, ECS services, and on-premises servers. |
| **Authentication** | AWS Cognito, Lambda authorizers for authentication and authorization. | AWS Cognito, OIDC, SAML 2.0 identity providers for authentication. |
| **Monitoring** | Detailed API monitoring through Amazon CloudWatch. | CloudWatch for basic monitoring, AWS X-Ray for detailed request tracing. |
| **Scaling** | Scales automatically with the number of API calls. | Scales automatically, distributing traffic according to routing rules. |
| **Use Cases** | Serverless architectures, RESTful API backends, real-time communication applications. | Load balancing HTTP/HTTPS traffic, microservice architectures. |
| **Cost** | Number of API calls, data transfer, and features like caching affect costs. | Charged based on Load Balancer Capacity Units (LCU) usage. |
| **Security** | Custom domain names with SSL/TLS certificates via AWS Certificate Manager. | Custom domain names with SSL/TLS certificates, advanced request routing for security. |
| **Deployment** | Managed service without infrastructure management. | Managed service, requires setup of target groups and health checks. |


## For exam

1. The product team at a startup has figured out a market need to support both stateful and stateless client-server communications via the application programming interface (APIs) developed using its platform. You have been hired by the startup as a solutions architect to build a solution to fulfill this market need using Amazon API Gateway.

Which of the following would you identify as correct?

```mermaid
graph LR
    A[Amazon API Gateway Solution] --> B[Stateless Communications]
    A --> C[Stateful Communications]
    A --> D[Building the Solution]

    B --> E[Stateless API]
    B --> F[Implementation]
    B --> G[Scalability]

    E --> H[RESTful APIs]
    F --> I[Define HTTP or HTTPS Endpoints]
    G --> J[Inherently Scalable]

    C --> K[Stateful API with WebSockets]
    C --> L[WebSocket API]
    C --> M[Connection Management]

    K --> N[Maintains Client Session State]
    L --> O[Persistent Two-way Connection]
    M --> P[Handles Connections and Messages]

    D --> Q[Design RESTful APIs]
    D --> R[Develop WebSocket APIs]
    D --> S[Backend Integration]
    D --> T[Security and Authentication]
    D --> U[Monitoring and Logging]

    Q --> V[Define Resources and Methods]
    R --> W[Setup for Persistent Connection]
    S --> X[Integrate with Backend Services]
    T --> Y[Implement API Security Measures]
    U --> Z[Use Amazon CloudWatch]

    X --> AA[AWS Lambda, Amazon ECS, EC2 Instances]
    Y --> AB[API Keys, IAM Roles, Authorizers]
    Z --> AC[Monitor Performance, Log Requests/Responses]

```

