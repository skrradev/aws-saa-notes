# SQS

```mermaid
graph LR
    A[Amazon SQS  Standard Queue] --> B[History]
B --> C[Oldest in its Category, Over 10 Years]

A --> D[Service Model]
D --> E[Fully Managed Service]
E --> F[Decouples Applications for Scalability]

A --> G[Attributes]
G --> H[Unlimited Throughput]
G --> I[Unlimited Messages in Queue]
G --> J[Message Retention: 4 to 14 Days]
G --> K[Low Latency: <10 Milliseconds]
G --> L[Message Size Limit: 256KB]

A --> M[Delivery Guarantees]
M --> N[At Least Once Delivery]
M --> O[Best Effort Ordering]

style A fill:#f9f,stroke:#333,stroke-width:4px
style B fill:#ccf,stroke:#333,stroke-width:2px
style D fill:#ccf,stroke:#333,stroke-width:2px
style G fill:#ccf,stroke:#333,stroke-width:2px
style M fill:#ccf,stroke:#333,stroke-width:2px


```

##  SQS  Producing Messages
```mermaid
graph LR
A[SQS  Producing Messages] --> B[SDK Usage]
B --> C[Use AWS SDK's SendMessage API]

    A --> D[Message Persistence]
    D --> E[Stored in Queue Until Processed and Deleted]

    A --> F[Retention Period]
    F --> G[Default: 4 Days, Max: 14 Days]

    A --> H[Example Use Case]
    H --> I[Sending an Order with Order ID, Customer ID, etc.]

    A --> J[Message Size Limit]
    J --> K[Max: 256 KB per Message]

    A --> L[Throughput]
    L --> M[Unlimited Throughput for Standard Queues]

    style A fill:#f9f,stroke:#333,stroke-width:4px
    style B fill:#ccf,stroke:#333,stroke-width:2px
    style D fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#ccf,stroke:#333,stroke-width:2px
    style H fill:#ccf,stroke:#333,stroke-width:2px
    style J fill:#ccf,stroke:#333,stroke-width:2px
    style L fill:#ccf,stroke:#333,stroke-width:2px

```



##  SQS  Amazon SQS Queue Consumers 
```mermaid
flowchart LR
sqs[SQS Queue] -->|Messages to| ec2[Multiple EC2 Instance Consumers]
sqs -->|At Least Once Delivery| ec2
sqs -->|Best-Effort Message Ordering| ec2
ec2 -->|Message Deletion| sqs
ec2 -->|Horizontal Scaling as needed| scale[Dynamic EC2 Scaling]

    classDef sqsClass fill:#f96,stroke:#333,stroke-width:2px;
    classDef ec2Class fill:#79f,stroke:#333,stroke-width:2px;
    classDef scaleClass fill:#ff9,stroke:#333,stroke-width:2px;

    class sqs sqsClass;
    class ec2 ec2Class;
    class scale scaleClass;

```

##  SQS  Amazon SQS Queue ASG
```mermaid
flowchart LR
sqs[SQS Queue] -->|Messages to be processed| ec2[(EC2 Instances)]
ec2 --> asg[Auto Scaling Group ASG]
asg -->|Scales in/out based on demand| cw[CloudWatch Metric - Queue Length]
cw -->|Triggers scaling| alarm[CloudWatch Alarm]
ec2 -->|Poll for Messages| sqs

    classDef sqsClass fill:#f96,stroke:#333,stroke-width:2px;
    classDef ec2Class fill:#79f,stroke:#333,stroke-width:2px;
    classDef asgClass fill:#ff9,stroke:#333,stroke-width:2px;
    classDef cwClass fill:#9f9,stroke:#333,stroke-width:2px;
    classDef alarmClass fill:#e6b8af,stroke:#333,stroke-width:2px;

    class sqs sqsClass;
    class ec2 ec2Class;
    class asg asgClass;
    class cw cwClass;
    class alarm alarmClass;

```

##  SQS  Amazon SQS Queue Decoupling
```mermaid
graph TB
A[Front-end Web App] -->|Send Message to| B[SQS Queue]
A -->|Auto-Scaling| A
B -->|Receive Messages from| D[Back-end Processing Application Video Processing]
D -->|Insert into| E[Amazon S3]
D -->|Auto-Scaling for Back-end| D

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef processing fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef storage fill:#ddf,stroke:#333,stroke-width:2px;
    
    class B default;
    class D processing;
    class E storage;

```


##  SQS  Amazon SQS Security Features
```mermaid
graph LR
A[Amazon SQS Security Features] --> B[Encryption]
B --> C[In-flight Encryption: HTTPS]
B --> D[At-rest Encryption: AWS KMS Keys]
B --> E[Client-side Encryption: Optional]

    A --> F[Access Controls]
    F --> G[IAM Policies for Send/Receive Access]

    A --> H[SQS Access Policies]
    H --> I[Cross-Account Permissions]
    H --> J[Interaction with Other AWS Services]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef encryption fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef access fill:#ddf,stroke:#333,stroke-width:2px;
    
    class B encryption;
    class F,H access;
```

##    Amazon SQS  Visibility Timeout
```mermaid
sequenceDiagram
participant C as Consumer
participant SQS as SQS Queue
participant T as Timeout

    C->>SQS: ReceiveMessage request
    Note over SQS: Message becomes invisible
    SQS->>C: Message delivered
    C->>T: Start Visibility Timeout (e.g., 30s)
    Note over C,T: Consumer processes message
    alt if more time needed
        C->>SQS: ChangeMessageVisibility
        Note over SQS: Extend Visibility Timeout
    end
    alt if message processed within extended timeout
        C->>SQS: DeleteMessage request
        Note over SQS: Message deleted from queue
    else if extended timeout expires
        T->>SQS: Message becomes visible again
        SQS->>C: Message can be received again
    end

```

##  SQS  Amazon SQS Long Polling
```mermaid

flowchart TD
A[Amazon SQS Long Polling] --> B[Long Polling]
B -->|Wait for messages| C[Efficiency]
C -->|Reduces empty responses| D[Wait Time]
D -->|1 to 20 seconds| E[Comparison with Short Polling]
E -->|More efficient than Short Polling| F[Configuration]
F -->|Enabled at queue or API level| G[WaitTimeSeconds Parameter]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef important fill:#ff9,stroke:#333,stroke-width:2px;

    class B,E important;

```

##  Amazon SQS FIFO Queues
```mermaid
graph LR
A[Amazon SQS FIFO Queues] --> B[FIFO First In First Out]
B --> C[Message Ordering]
A --> D[Throughput Limits]
D --> E[300 msg/sec without batching]
D --> F[3000 msg/sec with batching]
A --> G[Exactly-Once Processing]
G --> H[Eliminates Duplicate Messages]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef processing fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef limit fill:#ddf,stroke:#333,stroke-width:2px;
    
    class B default;
    class D limit;
    class G processing;

```

##  Amazon SQS Queue ASG
```mermaid
graph TD
A[SQS Queue] -->|Triggers based on message count| B[CloudWatch Metric - Queue Length]
B -->|Monitors message queue length| C[CloudWatch Alarm]
C -->|Trigger ASG actions| D[Auto Scaling Group ASG]
D -->|Scale in/out| E[EC2 Instances]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef metric fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef alarm fill:#ddf,stroke:#333,stroke-width:2px;
    classDef asg fill:#ff9,stroke:#333,stroke-width:2px;
    
    class A default;
    class B metric;
    class C alarm;
    class D asg;
    class E default;

```

```mermaid
graph TD
A[Requests] -->|Handled by| B[Auto-Scaling Resources]
B -->|Enqueue Message| C[SendMessage to SQS]
C --> D[SQS Queue]
D -->|Poll messages| E[ReceiveMessages from Consumers]
E -->|Dequeue Message| F[Process Message]
F -->|Insert Data| G[Database]

    classDef default fill:#f9f,stroke:#333,stroke-width:2px;
    classDef process fill:#e6e6e6,stroke:#333,stroke-width:2px;
    classDef queue fill:#ddf,stroke:#333,stroke-width:2px;
    classDef database fill:#ff9,stroke:#333,stroke-width:2px;
    
    class A,B process;
    class C,D queue;
    class E,F process;
    class G database;

```
