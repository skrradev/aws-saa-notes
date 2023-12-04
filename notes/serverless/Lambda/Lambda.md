# Lambda

```mermaid
graph LR
    A[Amazon EC2] -->|Infrastructure| B[Virtual Servers in the Cloud]
    A -->|Capacity Limitation| C[Limited by RAM and CPU]
    A -->|Operation| D[Continuously Running]
    A -->|Scaling| E[Scaling Requires Intervention]

    F[AWS Lambda] -->|Infrastructure| G[Virtual Functions - No Servers to Manage]
    F -->|Execution Limitation| H[Limited by Time - Short Executions]
    F -->|Operation| I[Run On-Demand]
    F -->|Scaling| J[Scaling is Automated]

    classDef aws fill:#ff9900,stroke:#333,stroke-width:2px;
    classDef ec2 fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef lambda fill:#99ccff,stroke:#333,stroke-width:2px;

    class A,F aws;
    class B,C,D,E ec2;
    class G,H,I,J lambda;



```

```mermaid
graph LR
A[AWS Lambda] -->|Pricing Model| B[Easy Pricing]
A -->|Integration| C[AWS Integration]
A -->|Flexibility| D[Support for Multiple Programming Languages]
A -->|Monitoring| E[Monitoring with AWS CloudWatch]
A -->|Resource Management| F[Resource Allocation]

    classDef aws fill:#ff9900,stroke:#333,stroke-width:2px;
    classDef lambdaFeatures fill:#99ccff,stroke:#333,stroke-width:2px;

    class A aws;
    class B,C,D,E,F lambdaFeatures;
```

```mermaid
graph LR
AWS_Lambda[AWS Lambda] --> NodeJS[Node.js JavaScript]
AWS_Lambda --> Python[Python]
AWS_Lambda --> Java[Java Java 8 compatible]
AWS_Lambda --> CSharp[C# .NET Core]
AWS_Lambda --> Golang[Golang]
AWS_Lambda --> CSharp_PowerShell[C# / PowerShell]
AWS_Lambda --> Ruby[Ruby]
AWS_Lambda --> Custom_Runtime_API[Custom Runtime API e.g., Rust]
AWS_Lambda --> Lambda_Container_Image[Lambda Container Image]

    NodeJS --> NodeJS_Details["Asynchronous operations"]
    Python --> Python_Details["Web services, Data analysis"]
    Java --> Java_Details["Class-based, Object-oriented"]
    CSharp --> CSharp_Details[".NET, Cross-platform"]
    Golang --> Golang_Details["Statically typed, Similar to C"]
    CSharp_PowerShell --> CSharp_PowerShell_Details["Task automation, Configuration management"]
    Ruby --> Ruby_Details["Dynamic, Productivity-focused"]
    Custom_Runtime_API --> Custom_Runtime_API_Details["Flexible, Community supported"]
    Lambda_Container_Image --> Lambda_Container_Image_Details["Container images, ECS/Fargate for Docker"]
```

## Integrations
```mermaid
graph LR
AWS_Lambda[AWS Lambda] --> API_Gateway[API Gateway]
AWS_Lambda --> Kinesis[Kinesis]
AWS_Lambda --> DynamoDB[DynamoDB]
AWS_Lambda --> S3[S3]
AWS_Lambda --> CloudFront[CloudFront]
AWS_Lambda --> CloudWatch_Events[CloudWatch Events / EventBridge]
AWS_Lambda --> CloudWatch_Logs[CloudWatch Logs]
AWS_Lambda --> SNS[SNS]
AWS_Lambda --> SQS[SQS]
AWS_Lambda --> Cognito[Cognito]

    API_Gateway --> API_Details["Trigger for HTTP requests"]
    Kinesis --> Kinesis_Details["Real-time data processing"]
    DynamoDB --> DynamoDB_Details["Respond to table changes"]
    S3 --> S3_Details["Trigger on file operations"]
    CloudFront --> CloudFront_Details["Content customization with Lambda@Edge"]
    CloudWatch_Events --> CW_Events_Details["Trigger on AWS resource changes"]
    CloudWatch_Logs --> CW_Logs_Details["Trigger on log events"]
    SNS --> SNS_Details["Process pub/sub notifications"]
    SQS --> SQS_Details["Process queued messages"]
    Cognito --> Cognito_Details["Custom authentication, User data handling"]
```
## Use cases
```mermaid
graph TD
Trigger[1. Trigger: Image uploaded to S3] --> Lambda_Function[2. AWS Lambda Function]
Lambda_Function --> Create_Thumbnail[3. Create a Thumbnail]
Create_Thumbnail --> New_Thumbnail_S3[4. New Thumbnail in S3]
New_Thumbnail_S3 --> Metadata_DynamoDB[5. Metadata in DynamoDB]

    style Trigger fill:#f9f,stroke:#333,stroke-width:2px
    style Lambda_Function fill:#fcf,stroke:#333,stroke-width:2px
    style Create_Thumbnail fill:#cff,stroke:#333,stroke-width:2px
    style New_Thumbnail_S3 fill:#cfc,stroke:#333,stroke-width:2px
    style Metadata_DynamoDB fill:#cff,stroke:#333,stroke-width:2px
```
```mermaid
graph TD
CloudWatch[1. CloudWatch Events / EventBridge] --> Trigger[2. Trigger]
Trigger --> Lambda_Function[3. AWS Lambda Function]
Lambda_Function --> Perform_Task[4. Perform a Task]

    style CloudWatch fill:#f9f,stroke:#333,stroke-width:2px
    style Trigger fill:#fcf,stroke:#333,stroke-width:2px
    style Lambda_Function fill:#cff,stroke:#333,stroke-width:2px
    style Perform_Task fill:#cfc,stroke:#333,stroke-width:2px
```
## AWS Lambda Pricing

```mermaid
graph LR
AWS_Lambda_Pricing[AWS Lambda Pricing] --> Pay_per_Calls[Pay per Calls]
AWS_Lambda_Pricing --> Pay_per_Duration[Pay per Duration]

    Pay_per_Calls --> Free_Calls[First 1,000,000 requests/month: Free]
    Pay_per_Calls --> Paid_Calls[After free tier: $0.20 per 1 million requests]

    Pay_per_Duration --> Free_Duration[400,000 GB-seconds/month free]
    Pay_per_Duration --> Compute_Time_Details[Compute Time: 1 GB RAM = 400,000s, 128 MB RAM = 3,200,000s]
    Pay_per_Duration --> Paid_Duration[Beyond free tier: $1.00 per 600,000 GB-seconds]

    style AWS_Lambda_Pricing fill:#f9f,stroke:#333,stroke-width:2px
    style Pay_per_Calls fill:#fcf,stroke:#333,stroke-width:2px
    style Pay_per_Duration fill:#cff,stroke:#333,stroke-width:2px
    style Free_Calls fill:#cfc,stroke:#333,stroke-width:2px
    style Paid_Calls fill:#cfc,stroke:#333,stroke-width:2px
    style Free_Duration fill:#cfc,stroke:#333,stroke-width:2px
    style Compute_Time_Details fill:#cff,stroke:#333,stroke-width:2px
    style Paid_Duration fill:#cfc,stroke:#333,stroke-width:2px
```


## AWS Lambda Limits

```mermaid
graph LR
AWS_Lambda_Limits[AWS Lambda Limits] --> Execution[Execution]
AWS_Lambda_Limits --> Deployment[Deployment]

    Execution --> Memory_Allocation[Memory allocation: 128 MB to 10 GB]
    Execution --> Max_Execution_Time[Maximum execution time: 900s]
    Execution --> Env_Variables_Size[Environment variables: 4 KB]
    Execution --> Disk_Capacity[Disk capacity in /tmp: 512 MB to 10 GB]
    Execution --> Concurrency[Concurrency executions: 1000 increasable]

    Deployment --> Function_Deployment_Size[Lambda function deployment size: 50 MB compressed]
    Deployment --> Uncompressed_Deployment_Size[Uncompressed deployment: 250 MB]
    Deployment --> Tmp_Directory_Use[Use of /tmp directory for additional files]
    Deployment --> Env_Variables_Deployment[Size of environment variables: 4 KB]

    style AWS_Lambda_Limits fill:#f9f,stroke:#333,stroke-width:2px
    style Execution fill:#fcf,stroke:#333,stroke-width:2px
    style Deployment fill:#cff,stroke:#333,stroke-width:2px
    style Memory_Allocation fill:#cfc,stroke:#333,stroke-width:2px
    style Max_Execution_Time fill:#cfc,stroke:#333,stroke-width:2px
    style Env_Variables_Size fill:#cfc,stroke:#333,stroke-width:2px
    style Disk_Capacity fill:#cfc,stroke:#333,stroke-width:2px
    style Concurrency fill:#cfc,stroke:#333,stroke-width:2px
    style Function_Deployment_Size fill:#cfc,stroke:#333,stroke-width:2px
    style Uncompressed_Deployment_Size fill:#cfc,stroke:#333,stroke-width:2px
    style Tmp_Directory_Use fill:#cfc,stroke:#333,stroke-width:2px
    style Env_Variables_Deployment fill:#cfc,stroke:#333,stroke-width:2px
```

## Customization At The Edge

```mermaid

graph TD
Customization_Edge[Customization At The Edge] --> Edge_Function[Edge Function]
Edge_Function --> CloudFront_Functions[CloudFront Functions]
Edge_Function --> Lambda_Edge[Lambda at Edge]

    CloudFront_Functions --> Advantages[Key Advantages]
    Lambda_Edge --> Advantages

    Advantages --> Serverless_Management["No server management"]
    Advantages --> Global_Deployment["Global deployment"]
    Advantages --> CDN_Customization["Customization of CDN content"]
    Advantages --> Pay_For_Use["Pay-for-use pricing"]
    Advantages --> Focus_On_Code["Focus on code (serverless)"]

    style Customization_Edge fill:#f9f,stroke:#333,stroke-width:2px
    style Edge_Function fill:#fcf,stroke:#333,stroke-width:2px
    style CloudFront_Functions fill:#cff,stroke:#333,stroke-width:2px
    style Lambda_Edge fill:#cff,stroke:#333,stroke-width:2px
    style Advantages fill:#cff,stroke:#333,stroke-width:2px
    style Serverless_Management fill:#cfc,stroke:#333,stroke-width:2px
    style Global_Deployment fill:#cfc,stroke:#333,stroke-width:2px
    style CDN_Customization fill:#cfc,stroke:#333,stroke-width:2px
    style Pay_For_Use fill:#cfc,stroke:#333,stroke-width:2px
    style Focus_On_Code fill:#cfc,stroke:#333,stroke-width:2px
```

## AWS Services: CloudFront Functions & Lambda at Edge

```mermaid
graph LR
AWS_Services[AWS Services: CloudFront Functions & Lambda at Edge] --> Website_Security[1. Website Security and Privacy]
AWS_Services --> Dynamic_Web_Application[2. Dynamic Web Application at the Edge]
AWS_Services --> SEO[3. Search Engine Optimization SEO]
AWS_Services --> Routing[4. Intelligently Route Across Origins and Data Centers]
AWS_Services --> Bot_Mitigation[5. Bot Mitigation at the Edge]
AWS_Services --> Image_Transformation[6. Real-time Image Transformation]
AWS_Services --> AB_Testing[7. A/B Testing]
AWS_Services --> User_Auth[8. User Authentication and Authorization]
AWS_Services --> User_Prioritization[9. User Prioritization]
AWS_Services --> User_Tracking[10. User Tracking and Analytics]

    style AWS_Services fill:#f9f,stroke:#333,stroke-width:2px
    style Website_Security fill:#fcf,stroke:#333,stroke-width:2px
    style Dynamic_Web_Application fill:#cff,stroke:#333,stroke-width:2px
    style SEO fill:#cff,stroke:#333,stroke-width:2px
    style Routing fill:#cff,stroke:#333,stroke-width:2px
    style Bot_Mitigation fill:#cff,stroke:#333,stroke-width:2px
    style Image_Transformation fill:#cff,stroke:#333,stroke-width:2px
    style AB_Testing fill:#cff,stroke:#333,stroke-width:2px
    style User_Auth fill:#cff,stroke:#333,stroke-width:2px
    style User_Prioritization fill:#cff,stroke:#333,stroke-width:2px
    style User_Tracking fill:#cff,stroke:#333,stroke-width:2px
```

## CloudFront Functions

```mermaid
graph LR
CloudFront_Functions[CloudFront Functions] --> Lightweight_Functions[Lightweight Functions]
CloudFront_Functions --> High_Scale_Latency[High Scale and Latency Sensitivity]
CloudFront_Functions --> Viewer_Interaction[Viewer Request and Response]
CloudFront_Functions --> Native_Feature[Native CloudFront Feature]

    Lightweight_Functions --> JS_Code["Small JavaScript code pieces"]
    High_Scale_Latency --> Handling_Requests["Handle millions of requests/sec"]
    High_Scale_Latency --> Startup_Times["Sub-millisecond startup times"]
    Viewer_Interaction --> Viewer_Request[Viewer Request]
    Viewer_Interaction --> Viewer_Response[Viewer Response]
    Native_Feature --> Runs_In_CloudFront["Runs within CloudFront"]

    style CloudFront_Functions fill:#f9f,stroke:#333,stroke-width:2px
    style Lightweight_Functions fill:#fcf,stroke:#333,stroke-width:2px
    style High_Scale_Latency fill:#cff,stroke:#333,stroke-width:2px
    style Viewer_Interaction fill:#cff,stroke:#333,stroke-width:2px
    style Native_Feature fill:#cff,stroke:#333,stroke-width:2px
    style JS_Code fill:#cfc,stroke:#333,stroke-width:2px
    style Handling_Requests fill:#cfc,stroke:#333,stroke-width:2px
    style Startup_Times fill:#cfc,stroke:#333,stroke-width:2px
    style Viewer_Request fill:#cfc,stroke:#333,stroke-width:2px
    style Viewer_Response fill:#cfc,stroke:#333,stroke-width:2px
    style Runs_In_CloudFront fill:#cfc,stroke:#333,stroke-width:2px
```


## Lambda at Edge

```mermaid
graph LR
Lambda_Edge[Lambda at Edge] --> Scalability[Scalability]
Lambda_Edge --> Function_Triggers[Function Triggers]
Lambda_Edge --> Authoring_Replication[Authoring and Replication]

    Scalability --> High_Traffic_Support["Scales to thousands of requests/sec"]

    Function_Triggers --> Viewer_Request[Viewer Request]
    Function_Triggers --> Origin_Request[Origin Request]
    Function_Triggers --> Origin_Response[Origin Response]
    Function_Triggers --> Viewer_Response[Viewer Response]

    Viewer_Request --> Modify_Requests["Modify incoming requests"]
    Origin_Request --> Modify_Origin_Requests["Modify requests to origin"]
    Origin_Response --> Modify_Origin_Response["Modify responses from origin"]
    Viewer_Response --> Modify_Viewer_Response["Modify responses to viewers"]

    Authoring_Replication --> Single_Region_Authoring["Create/manage in one AWS Region"]
    Authoring_Replication --> Global_Replication["Automatically replicated worldwide"]

    style Lambda_Edge fill:#f9f,stroke:#333,stroke-width:2px
    style Scalability fill:#fcf,stroke:#333,stroke-width:2px
    style Function_Triggers fill:#cff,stroke:#333,stroke-width:2px
    style Authoring_Replication fill:#cff,stroke:#333,stroke-width:2px
    style High_Traffic_Support fill:#cfc,stroke:#333,stroke-width:2px
    style Viewer_Request fill:#cfc,stroke:#333,stroke-width:2px
    style Origin_Request fill:#cfc,stroke:#333,stroke-width:2px
    style Origin_Response fill:#cfc,stroke:#333,stroke-width:2px
    style Viewer_Response fill:#cfc,stroke:#333,stroke-width:2px
    style Modify_Requests fill:#cfc,stroke:#333,stroke-width:2px
    style Modify_Origin_Requests fill:#cfc,stroke:#333,stroke-width:2px
    style Modify_Origin_Response fill:#cfc,stroke:#333,stroke-width:2px
    style Modify_Viewer_Response fill:#cfc,stroke:#333,stroke-width:2px
    style Single_Region_Authoring fill:#cfc,stroke:#333,stroke-width:2px
    style Global_Replication fill:#cfc,stroke:#333,stroke-width:2px
```

# CloudFront Functions vs. Lambda@Edge Comparison

| Feature                 | CloudFront Functions        | Lambda@Edge                |
|-------------------------|-----------------------------|----------------------------|
| **Runtime Support**     | JavaScript                  | Node.js, Python            |
| **# of Requests**       | Millions per second         | Thousands per second       |
| **CloudFront Triggers** | Viewer Request/Response     | Viewer Request/Response, Origin Request/Response |
| **Max. Execution Time** | < 1 ms                      | 5 – 10 seconds             |
| **Max. Memory**         | 2 MB                        | 128 MB up to 10 GB         |
| **Total Package Size**  | 10 KB                       | 1 MB – 50 MB               |
| **Network Access**      | No                          | Yes                        |
| **File System Access**  | No                          | Yes                        |
| **Access to Request Body** | No                       | Yes                        |
| **Pricing**             | Free tier available, 1/6th price of Lambda@Edge | No free tier, charged per request & duration |

## Notes
- CloudFront Functions are designed for high-scale, latency-sensitive CDN customizations.
- Lambda@Edge allows for more complex computing at the edge with higher computational and memory capacity.
- Pricing models differ significantly, with CloudFront Functions aimed at cost efficiency for simple tasks.


## CloudFront Functions Lambda@Edge

```mermaid
graph LR
subgraph CloudFront_Functions [CloudFront Functions]
Cache_Key_Normalization[Cache Key Normalization]
Header_Manipulation[Header Manipulation]
URL_Rewrites_Redirects[URL Rewrites or Redirects]
Request_Auth[Request Authentication & Authorization]
end

    subgraph Lambda_Edge [Lambda@Edge]
    Longer_Execution[Longer Execution Time]
    Adjustable_CPU_Memory[Adjustable CPU or Memory]
    Code_Dependencies[Code Dependencies]
    Network_Access[Network Access]
    FileSystem_Access[File System Access]
    end

    style CloudFront_Functions fill:#f9f,stroke:#333,stroke-width:2px
    style Cache_Key_Normalization fill:#cfc,stroke:#333,stroke-width:2px
    style Header_Manipulation fill:#cfc,stroke:#333,stroke-width:2px
    style URL_Rewrites_Redirects fill:#cfc,stroke:#333,stroke-width:2px
    style Request_Auth fill:#cfc,stroke:#333,stroke-width:2px

    style Lambda_Edge fill:#fcf,stroke:#333,stroke-width:2px
    style Longer_Execution fill:#cff,stroke:#333,stroke-width:2px
    style Adjustable_CPU_Memory fill:#cff,stroke:#333,stroke-width:2px
    style Code_Dependencies fill:#cff,stroke:#333,stroke-width:2px
    style Network_Access fill:#cff,stroke:#333,stroke-width:2px
    style FileSystem_Access fill:#cff,stroke:#333,stroke-width:2px
```

## Lambda by Default

```mermaid
graph TD
Lambda_Default[Lambda by Default] -->|Runs In| Default_AWS_VPC[Default AWS Managed VPC]
Lambda_Default -->|Cannot Access| No_Access_User_VPC[Resources in User's VPC]

    Default_AWS_VPC --> Internet_Access[Can Access Internet]
    Default_AWS_VPC --> Public_AWS_Services[Can Access Public AWS Services]
    No_Access_User_VPC --> No_Private_RDS[No Access to Private RDS]
    No_Access_User_VPC --> No_ElastiCache[No Access to ElastiCache]
    No_Access_User_VPC --> No_Private_ELB[No Access to Internal ELB]

    subgraph Additional Configuration for VPC Access
    Config_Lambda_VPC[Configure Lambda to Run Within User's VPC]
    Config_Lambda_VPC --> Set_Security_Groups[Set Up Security Groups]
    Config_Lambda_VPC --> Set_ACLs[Set Up Network ACLs]
    end

    style Lambda_Default fill:#f9f,stroke:#333,stroke-width:2px
    style Default_AWS_VPC fill:#cff,stroke:#333,stroke-width:2px
    style No_Access_User_VPC fill:#cff,stroke:#333,stroke-width:2px
    style Internet_Access fill:#cfc,stroke:#333,stroke-width:2px
    style Public_AWS_Services fill:#cfc,stroke:#333,stroke-width:2px
    style No_Private_RDS fill:#fcf,stroke:#333,stroke-width:2px
    style No_ElastiCache fill:#fcf,stroke:#333,stroke-width:2px
    style No_Private_ELB fill:#fcf,stroke:#333,stroke-width:2px
    style Config_Lambda_VPC fill:#fcf,stroke:#333,stroke-width:4px
    style Set_Security_Groups fill:#cfc,stroke:#333,stroke-width:2px
    style Set_ACLs fill:#cfc,stroke:#333,stroke-width:2px
```
## Lambda in VPC

```mermaid
graph LR
Lambda_VPC[Lambda in VPC] -->|Configures With| VPC_ID[VPC ID]
Lambda_VPC -->|Configures With| Subnets[Subnets]
Lambda_VPC -->|Configures With| Security_Groups[Security Groups]

    VPC_ID --> ENI[Elastic Network Interface ENI]
    Subnets --> ENI
    Security_Groups --> ENI

    ENI --> Lambda_Function[Lambda Function]
    ENI --> RDS[RDS Instance]

    Lambda_Function --> Interact_RDS[Can Interact with RDS]
    RDS --> Own_Security_Group[RDS Security Group]

    style Lambda_VPC fill:#f9f,stroke:#333,stroke-width:2px
    style VPC_ID fill:#cff,stroke:#333,stroke-width:2px
    style Subnets fill:#cff,stroke:#333,stroke-width:2px
    style Security_Groups fill:#cff,stroke:#333,stroke-width:2px
    style ENI fill:#fcf,stroke:#333,stroke-width:2px
    style Lambda_Function fill:#cfc,stroke:#333,stroke-width:2px
    style RDS fill:#cfc,stroke:#333,stroke-width:2px
    style Interact_RDS fill:#cfc,stroke:#333,stroke-width:2px
    style Own_Security_Group fill:#fcf,stroke:#333,stroke-width:2px
```

## Lambda with RDS Proxy

```mermaid
graph TD
Lambda_RDS_Proxy[Lambda with RDS Proxy] -->|Manages Connections to| RDS_Proxy[RDS Proxy]
RDS_Proxy -->|Connection Pooling| Improved_Scalability[Improved Scalability]
RDS_Proxy -->|Reduced Failover Times| Increased_Availability[Increased Availability]
RDS_Proxy -->|Enhanced Security| Enhanced_Security[Enhanced Security]

    Lambda_Functions[Multiple Lambda Functions] -->|Within VPC| Lambda_RDS_Proxy
    RDS_Proxy -->|In Private Subnet| RDS_Instance[RDS Instance]
    Lambda_Functions -->|Connect via RDS Proxy| RDS_Instance

    Enhanced_Security -->|IAM Integration| IAM_Auth[Uses IAM for Authentication]
    Enhanced_Security -->|Secrets Manager| Secrets_Manager[Uses AWS Secrets Manager]

    style Lambda_RDS_Proxy fill:#f9f,stroke:#333,stroke-width:2px
    style RDS_Proxy fill:#cff,stroke:#333,stroke-width:2px
    style Improved_Scalability fill:#cfc,stroke:#333,stroke-width:2px
    style Increased_Availability fill:#cfc,stroke:#333,stroke-width:2px
    style Enhanced_Security fill:#cff,stroke:#333,stroke-width:2px
    style Lambda_Functions fill:#fcf,stroke:#333,stroke-width:2px
    style RDS_Instance fill:#cfc,stroke:#333,stroke-width:2px
    style IAM_Auth fill:#cfc,stroke:#333,stroke-width:2px
    style Secrets_Manager fill:#cfc,stroke:#333,stroke-width:2px
```

