---
title: "AWS Infrastructure Monitoring and Logging"
date: 2026-10-30
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---

#### Overview

This section introduces the monitoring and logging services used to observe the AWS infrastructure deployed in this project.

AWS provides several services that help administrators monitor resource performance, record account activities, and review resource configurations.

The main services considered in this project include:

- **Amazon CloudWatch:** Monitors AWS resource metrics and operational information.
- **AWS CloudTrail:** Records account activities and API events.
- **AWS Config:** Records resource configurations and evaluates them against configuration rules.

These services provide information that helps administrators review infrastructure activities and identify potential configuration or operational issues.

#### 1. Prepare the Monitoring Environment

Before reviewing the monitoring services, verify that the following AWS resources are available:

- An EC2 instance named `KLTN-Web-Server`.
- An Application Load Balancer named `KLTN-ALB`.
- An RDS MySQL instance named `kltn-db`.
- Access to the AWS Management Console.
- The appropriate IAM permissions to view monitoring and logging information.

The monitoring services are reviewed in the AWS Region `ap-southeast-1` (Singapore), where the project's infrastructure is deployed.

#### 2. Monitor EC2 Metrics with Amazon CloudWatch

Amazon CloudWatch collects and displays metrics from AWS resources.

To review EC2 monitoring information:

1. Open the AWS Management Console.
2. Navigate to **CloudWatch**.
3. Select **Metrics**.
4. Open the EC2 metric category.
5. Review the available metrics for the EC2 instance.

Common EC2 metrics include:

- `CPUUtilization`: CPU utilization.
- `NetworkIn`: Incoming network traffic.
- `NetworkOut`: Outgoing network traffic.
- `NetworkPacketsIn`: Incoming network packets.
- `NetworkPacketsOut`: Outgoing network packets.

These metrics help administrators observe the performance and network activity of the EC2 instance.

#### 3. Review AWS CloudTrail Events

AWS CloudTrail records account activities and API events performed within an AWS account.

To review CloudTrail information:

1. Open the AWS Management Console.
2. Navigate to **CloudTrail**.
3. Select **Event history**.
4. Review recent management events.
5. Filter events by event name, resource, or user identity when necessary.

CloudTrail helps administrators identify actions performed on AWS resources, including resource creation, configuration changes, and access-related activities.

#### 4. Review Resource Configuration with AWS Config

AWS Config helps track resource configurations and evaluate them against configuration rules.

In this project, AWS Config recording was enabled to collect information about AWS resources.

To review the configuration information:

1. Open the AWS Management Console.
2. Navigate to **AWS Config**.
3. Review the resource inventory.
4. Open the configuration timeline of a resource when necessary.
5. Review the compliance status of the configured rules.

AWS Config provides information about resource configuration changes and helps identify resources that may not satisfy the defined rules.

**Note:** Compliance results depend on the rules configured in AWS Config. A resource should not be described as compliant unless the corresponding evaluation result confirms it.

#### 5. Review Monitoring and Logging Results

After reviewing the services, administrators can use the collected information to understand the operational status of the AWS environment.

The following table summarizes the role of each service:

| AWS Service | Main Purpose |
|---|---|
| Amazon CloudWatch | Monitor resource metrics |
| AWS CloudTrail | Record account activities and API events |
| AWS Config | Track resource configurations and evaluate compliance |

These services complement one another by providing different types of operational and security information.

#### Conclusion

In this section, Amazon CloudWatch, AWS CloudTrail, and AWS Config were reviewed as monitoring and logging services for the AWS infrastructure.

CloudWatch provides resource performance metrics, CloudTrail records account activities, and AWS Config tracks resource configurations and evaluates compliance.

Together, these services support infrastructure monitoring, configuration review, and security management in the AWS environment.