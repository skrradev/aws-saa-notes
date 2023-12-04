# CloudTrail

```mermaid
graph LR
    A[CloudTrail Console] -- View, Search, Download --> B[Audit Logs]
    C1[SDK] --> A
    C2[CLI] --> A
    C3[Console] --> A
    C4[IAM Users & Roles] --> A
    A -- Store Logs --> D1[CloudWatch Logs]
    A -- Store Logs --> D2[S3 Bucket]

    classDef aws fill:#FF9900,color:#fff,stroke:#232F3E,stroke-width:2px;
    class A,B,C1,C2,C3,C4,D1,D2 aws;


```

```mermaid
graph TD
    A[CloudTrail Events] --> B[Management Events]
    A --> C[Data Events]

    B --> D[Read Events]
    B --> E[Write Events]
    C --> F[S3 Object-Level Activity]
    C --> G[AWS Lambda Function Execution]

    D --> H[Example: Viewing EC2 Instances]
    E --> I[Example: Creating IAM Roles]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:2px;
    classDef aws fill:#FF9900,color:#fff,stroke:#232F3E,stroke-width:2px;
    class A,B,C defaultStyle;
    class D,E,F,G,H,I aws;

    subgraph Management Events
        D
        E
    end

    subgraph Data Events
        F
        G
    end

    subgraph Read Events [Examples]
        H
    end

    subgraph Write Events [Examples]
        I
    end


```

```mermaid
graph LR
A[CloudTrail Insights] --> B[Behavioral Analysis]
A --> C[Anomaly Detection]
A --> D[Visibility and Notifications]

    B --> E[Analyzes Normal Management Events]
    B --> F[Establishes Baseline of Activity Patterns]

    C --> G[Monitors Write Events]
    C --> H[Detects Deviations from Baseline]

    D --> I[Anomaly Appears in CloudTrail Console]
    D --> J[Event Details Sent to Amazon S3]
    D --> K[Generates Amazon EventBridge Event]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:2px;
    classDef aws fill:#FF9900,color:#fff,stroke:#232F3E,stroke-width:2px;
    class A,B,C,D defaultStyle;
    class E,F,G,H,I,J,K aws;

    subgraph Behavioral Analysis
        E
        F
    end

    subgraph Anomaly Detection
        G
        H
    end

    subgraph Visibility and Notifications
        I
        J
        K
    end

```

```mermaid
graph LR
A[CloudTrail Events Retention] --> B[Event Storage - 90 Days]
A --> C[Long-Term Retention - Amazon S3]
A --> D[Types of Events]
A --> E[Analysis with Athena]

    B --> F[View and Search in CloudTrail Console]

    C --> G[Compliance and Historical Analysis]
    
    D --> H[Management Events - Default Logging]
    D --> I[Data Events - Not Logged by Default]
    D --> J[Insights Events - Detected Unusual Activity]

    E --> K[Interactive SQL Queries on S3 Data]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:2px;
    classDef aws fill:#FF9900,color:#fff,stroke:#232F3E,stroke-width:2px;
    class A,B,C,D,E defaultStyle;
    class F,G,H,I,J,K aws;

    subgraph Event Storage
        F
    end

    subgraph Long-Term Retention
        G
    end

    subgraph Types of Events
        H
        I
        J
    end

    subgraph Analysis
        K
    end

```

```mermaid
graph TD
A[User Action - API Call to AWS] -->|Logged by CloudTrail| B[Logging the API Call]
B -->|Creates Event| C[Event Creation]
C -->|Processed by EventBridge| D[EventBridge Processing]
D -->|Rule Triggered| E[Alerting]
E -->|Sends Notification| F[Amazon SNS]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:2px;
    classDef aws fill:#FF9900,color:#fff,stroke:#232F3E,stroke-width:2px;
    class A,B,C,D,E,F defaultStyle;
    class B,C,D,E,F aws;

    subgraph AWS Services
        B
        D
        F
    end
```


```mermaid
graph TD
A[CloudTrail Trails] -->|Record API Activity| B[Trail Configuration]
B -->|Global or Single Region| C[Trail Scope]
C --> D[Service Specific Logging]
D --> E[API Actions Recorded]
E -->|Log to S3 Bucket| F[Log Storage]
F --> G[Aggregation Across Accounts]
G --> H[Free and Paid Options]

    I[CloudTrail Insights] -->|Analyze Write Management Events| J[Insights Configuration]
    J -->|Establish Baseline of Activity| K[Baseline Analysis]
    K -->|Continuous Analysis| L[Detect Unusual Activity]
    L -->|Generate Insight Events| M[Insights Events]
    M -->|Visibility in CloudTrail Console| N[Console Visibility]
    N -->|Trigger Responses or Alerts| O[Custom Responses]

    classDef defaultStyle fill:#f9f,stroke:#333,stroke-width:2px;
    classDef aws fill:#FF9900,color:#fff,stroke:#232F3E,stroke-width:2px;
    class A,B,C,D,E,F,G,H,I,J,K,L,M,N,O defaultStyle;
    class B,C,D,E,F,G,H,J,K,L,M,N,O aws;

    subgraph CloudTrail Features
        A
        I
    end
    subgraph Trails Details
        B
        C
        D
        E
        F
        G
        H
    end
    subgraph Insights Details
        J
        K
        L
        M
        N
        O
    end
```

## For exam
1. While consolidating logs for the weekly reporting, a development team at an e-commerce company noticed that an unusually large number of illegal AWS application programming interface (API) queries were made sometime during the week. Due to the off-season, there was no visible impact on the systems. However, this event led the management team to seek an automated solution that can trigger near-real-time warnings in case such an event recurs.

Which of the following represents the best solution for the given scenario?

***Answer:*** Create an Amazon CloudWatch metric filter that processes AWS CloudTrail logs having API call details and looks at any errors by factoring in all the error codes that need to be tracked. Create an alarm based on this metric's rate to send an Amazon SNS notification to the required team

AWS CloudTrail log data can be ingested into Amazon CloudWatch to monitor and identify your AWS account activity against security threats, and create a governance framework for security best practices. You can analyze log trail event data in CloudWatch using features such as Logs Insight, Contributor Insights, Metric filters, and CloudWatch Alarms.

AWS CloudTrail integrates with the Amazon CloudWatch service to publish the API calls being made to resources or services in the AWS account. The published event has invaluable information that can be used for compliance, auditing, and governance of your AWS accounts. Below we introduce several features available in CloudWatch to monitor API activity, analyze the logs at scale, and take action when malicious activity is discovered, without provisioning your infrastructure.

For the AWS Cloudtrail logs available in Amazon CloudWatch Logs, you can begin searching and filtering the log data by creating one or more metric filters. Use these metric filters to turn log data into numerical CloudWatch metrics that you can graph or set a CloudWatch Alarm on.

Note: AWS CloudTrail Insights helps AWS users identify and respond to unusual activity associated with write API calls by continuously analyzing CloudTrail management events.

Insights events are logged when AWS CloudTrail detects unusual write management API activity in your account. If you have AWS CloudTrail Insights enabled and CloudTrail detects unusual activity, Insights events are delivered to the destination Amazon S3 bucket for your trail. You can also see the type of insight and the incident time when you view Insights events on the CloudTrail console. Unlike other types of events captured in a CloudTrail trail, Insights events are logged only when CloudTrail detects changes in your account's API usage that differ significantly from the account's typical usage patterns.


```mermaid
graph LR
    A[Automated Warning System for AWS API Queries] --> B[Create Amazon CloudWatch Metric Filter]
    A --> C[Process AWS CloudTrail Logs]
    A --> D[Create CloudWatch Alarm for Notifications]

    B --> E[Filter for Illegal API Query Patterns]
    B --> F[Track Error Codes]

    C --> G[Monitor API Call Details]
    C --> H[Analyze Log Data]

    D --> I[Set Rate-Based Alarm]
    D --> J[Send Amazon SNS Notification to Team]

    A --> K[Management's Requirement for Automated Solution]
    K --> L[Respond to Unusual API Activity]
    L --> M[Ensure Near-Real-Time Alerting]

    A --> N[Compliance, Auditing, and Governance Framework]
    N --> O[Use CloudTrail Insights for Enhanced Monitoring]

```