# ASG

```mermaid
graph TD;
    ASG[("Auto Scaling Groups\n-")]
    ASG -->|Manages| Instances[("EC2 Instances\n-")]
    ASG -->|Responds to| Metrics[("CloudWatch Metrics\n-")]
    ASG -->|Defines| Policies[("Scaling Policies\n-")]
    ASG -->|Utilizes| LaunchConfig[("Launch Configurations/Templates\n-")]
    ASG -->|Provides| HA[("High Availability\n-")]
    ASG -->|Balances Across| AZs[("Availability Zones\n-")]
    ASG -->|Integrates with| LB[("Load Balancers\n-")]

    Instances -->|Automatic scaling| InstanceCount[("Increase/Decrease Count\n-")]
    Metrics -->|Performance metrics| CPUUtilization[("CPU Utilization\n-")]
    Metrics -->|Custom metrics| CustomMetrics[("Custom Metrics\n-")]
    Policies -->|Triggered by metrics| PolicyActions[("Scale Out/In Actions\n-")]
    LaunchConfig -->|Instance setup| SetupDetails[("AMI, Instance Type, Key Pair, etc.\n-")]
    HA -->|Replaces unhealthy| ReplaceUnhealthy[("Replace Unhealthy Instances\n-")]
    AZs -->|Distribute instances| DistributeInstances[("Distribute Instances Evenly\n-")]
    LB -->|Distributes traffic| TrafficDistribution[("Distribute Incoming Traffic\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class ASG,Instances,Metrics,Policies,LaunchConfig,HA,AZs,LB important;
```

## ASG Scaling Policies

```mermaid
graph TD;
    ASG_Scaling[("ASG Scaling Policies\n-")]
    ASG_Scaling -->|Adjusts based on demand| TargetTracking[("Target Tracking Scaling\n- Adjusts based on a specific metric like CPU utilization\n-")]
    ASG_Scaling -->|Executes at scheduled times| ScheduledActions[("Scheduled Actions\n- Executes at specified times, regardless of demand\n-")]
    ASG_Scaling -->|Reacts to specific CloudWatch alarms| StepScaling[("Step Scaling\n- Changes in scaling steps in response to CloudWatch alarms\n-")]
    ASG_Scaling -->|Predicts and scales preemptively| PredictiveScaling[("Predictive Scaling\n- Uses machine learning to schedule the right number of EC2 instances in advance\n-")]

    classDef classA fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class ASG_Scaling,TargetTracking,ScheduledActions,StepScaling,PredictiveScaling classA;


```


## ASG Target Tracking Scaling
```mermaid
graph TD;
    TTS[("Target Tracking Scaling")]
    TTS -->|Objective| MetricTarget[("Maintain Metric at Target Value")]
    TTS -->|Common Metrics| CommonMetrics[("Commonly Used Metrics\n- CPU Utilization\n- Request Count per Target\n-")]
    TTS -->|Custom Metrics| CustomMetrics[("Custom Metrics\n- Any Published Metric\n-")]
    TTS -->|Cooldown Period| CooldownPeriod[("Cooldown Period\n- After Scaling Action\n-")]
    TTS -->|Efficiency| Efficiency[("Improves Efficiency\n- Optimizes Costs\n-")]

    MetricTarget -->|Set Point| SetPoint[("Desired Level\n- e.g., 50% CPU Utilization\n-")]
    CommonMetrics -->|Predefined| PredefinedMetrics[("Predefined Metrics\n- Provided by AWS\n-")]
    CustomMetrics -->|Customization| MetricSpecification[("Metric Specification\n- Custom CloudWatch Metrics\n-")]
    CooldownPeriod -->|Stabilization| StabilizationTime[("Stabilization Time\n- No Further Adjustments\n-")]
    Efficiency -->|Automatic Adjustment| AutoAdjustment[("Automatic Adjustment\n- Based on Demand\n-")]

    classDef important fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class TTS,MetricTarget,CommonMetrics,CustomMetrics,CooldownPeriod,Efficiency important;


```



## ASG Scaling Metrics
```mermaid
graph TD;
ASG_Metrics[("ASG Scaling Metrics\n-")]
ASG_Metrics --> CPUUtilization[("CPU Utilization\n- Overall CPU usage\n-")]
ASG_Metrics --> NetworkIn[("Network In\n- Incoming network traffic\n-")]
ASG_Metrics --> NetworkOut[("Network Out\n- Outgoing network traffic\n-")]
ASG_Metrics --> RequestCount[("Request Count Per Target\n- Number of requests to the load balancer\n-")]
ASG_Metrics --> Latency[("Latency\n- Time taken to respond to requests\n-")]
ASG_Metrics --> CustomMetric[("Custom Metric\n- User-defined specific metric\n-")]

    classDef classA fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class ASG_Metrics,CPUUtilization,NetworkIn,NetworkOut,RequestCount,Latency,CustomMetric classA;
```





## ASG Scaling Cooldowns
```mermaid
graph TD;
Cooldown[("Scaling Cooldowns\n-")]
Cooldown -->|Purpose| PreventFlapping[("Prevent Flapping\n- Avoids rapid scale in/out\n-")]
Cooldown -->|Default Period| DefaultCooldown[("Default Cooldown\n- Typically 300 seconds\n-")]
Cooldown -->|Customization| CustomCooldown[("Custom Cooldown\n- Based on workload\n-")]
Cooldown -->|Cooldown Effect| CooldownImpact[("Cooldown Impact\n- Suspends scaling activities\n-")]

    PreventFlapping -->|Stabilization| Stabilize[("Stabilize Metrics\n- Allow metrics to normalize\n-")]
    DefaultCooldown -->|After Scaling| DefaultTimer[("Default Timer\n- After any scaling activity\n-")]
    CustomCooldown -->|Specific Policies| PolicyCooldown[("Policy-specific Cooldown\n- Override default settings\n-")]
    CooldownImpact -->|Scaling Processes| SuspendScaling[("Suspend Other Scaling Processes\n-")]

    classDef classA fill:#f9a,stroke:#333,stroke-width:2px,shape:rectangle;
    class Cooldown,PreventFlapping,DefaultCooldown,CustomCooldown,CooldownImpact classA;

```


## For exam:

1. The engineering team at a data analytics company has observed that its flagship application functions at its peak performance when the underlying Amazon Elastic Compute Cloud (Amazon EC2) instances have a CPU utilization of about 50%. The application is built on a fleet of Amazon EC2 instances managed under an Auto Scaling group. The workflow requests are handled by an internal Application Load Balancer that routes the requests to the instances.

As a solutions architect, what would you recommend so that the application runs near its peak performance state?

***Answer:*** Configure the Auto Scaling group to use target tracking policy and set the CPU utilization as the target metric with a target value of 50%

An Auto Scaling group contains a collection of Amazon EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management. An Auto Scaling group also enables you to use Amazon EC2 Auto Scaling features such as health check replacements and scaling policies.

With target tracking scaling policies, you select a scaling metric and set a target value. Amazon EC2 Auto Scaling creates and manages the CloudWatch alarms that trigger the scaling policy and calculates the scaling adjustment based on the metric and the target value. The scaling policy adds or removes capacity as required to keep the metric at, or close to, the specified target value.

For example, you can use target tracking scaling to:

Configure a target tracking scaling policy to keep the average aggregate CPU utilization of your Auto Scaling group at 50 percent. This meets the requirements specified in the given use-case and therefore, this is the correct option.

```mermaid
graph LR
    A[Optimizing EC2 Instance Performance for Data Analytics Application] --> B[Configure Auto Scaling Group]
    A --> C[Use Target Tracking Policy]
    A --> D[Set CPU Utilization as Target Metric]
    A --> E[Target Value of 50%]

    B --> F[Collection of EC2 Instances]
    B --> G[Automatic Scaling and Management]

    C --> H[Select Scaling Metric]
    C --> I[Set Target Value]

    D --> J[Create and Manage CloudWatch Alarms]
    D --> K[Adjust Scaling Based on Metric]

    E --> L[Keep CPU Utilization Around 50%]
    E --> M[Add or Remove Capacity as Needed]

    A --> N[Ensure Peak Performance of Application]
    N --> O[Maintain Balanced Load]

```


2. The payroll department at a company initiates several computationally intensive workloads on Amazon EC2 instances at a designated hour on the last day of every month. The payroll department has noticed a trend of severe performance lag during this hour. The engineering team has figured out a solution by using Auto Scaling Group for these Amazon EC2 instances and making sure that 10 Amazon EC2 instances are available during this peak usage hour. For normal operations only 2 Amazon EC2 instances are enough to cater to the workload.

As a solutions architect, which of the following steps would you recommend to implement the solution?

***Answer:*** Configure your Auto Scaling group by creating a scheduled action that kicks-off at the designated hour on the last day of the month. Set the desired capacity of instances to 10. This causes the scale-out to happen before peak traffic kicks in at the designated hour

Scheduled scaling allows you to set your own scaling schedule. For example, let's say that every week the traffic to your web application starts to increase on Wednesday, remains high on Thursday, and starts to decrease on Friday. You can plan your scaling actions based on the predictable traffic patterns of your web application. Scaling actions are performed automatically as a function of time and date.

A scheduled action sets the minimum, maximum, and desired sizes to what is specified by the scheduled action at the time specified by the scheduled action. For the given use case, the correct solution is to set the desired capacity to 10. When we want to specify a range of instances, then we must use min and max values.

```mermaid
graph LR
    A[Implementing Solution for Payroll Department Workloads] --> B[Use Auto Scaling Group for EC2 Instances]
    A --> C[Configure Scheduled Scaling Actions]
    A --> D[Normal vs. Peak Operation Needs]

    B --> E[Ensure 10 Instances During Peak Hour]
    B --> F[Maintain 2 Instances for Normal Operations]

    C --> G[Schedule to Kick-off Last Day of the Month]
    C --> H[Set Desired Capacity to 10 Before Peak Hour]
    C --> I[Automated Scaling Based on Time/Date]

    D --> J[Computationally Intensive Workloads Monthly]
    D --> K[Performance Lag Observed Without Scaling]

    A --> L[Recommendation as Solutions Architect]
    L --> M[Optimize Performance and Resource Usage]
    M --> N[Balance Cost and Computational Needs]

```