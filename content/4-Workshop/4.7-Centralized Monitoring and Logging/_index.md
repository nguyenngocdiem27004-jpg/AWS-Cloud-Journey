---
title: "AWS Infrastructure Monitoring and Logging"
date: 2026-10-30
weight: 7
chapter: false
pre: " <b> 4.7. </b> "
---

#### Overview

Monitoring, logging, and configuration tracking are essential for maintaining the security and reliability of AWS infrastructure.

This project uses Amazon CloudWatch, AWS CloudTrail, AWS Config, Amazon EventBridge, and Amazon SNS to observe resource activity, record account events, evaluate configurations, and notify administrators about selected security-related changes.

### 1. Amazon CloudWatch

Amazon CloudWatch collects and displays monitoring data for AWS resources.

In this project, CloudWatch is used to review EC2 metrics and observe monitoring information related to security event processing.

To review CloudWatch:

1. Open the **CloudWatch** service.
2. Select **Metrics**.
3. Review the available EC2 metrics.
4. Select the relevant instance metrics.
5. Review graphs for CPU utilization and other available measurements.

CloudWatch helps administrators understand resource performance and identify unusual changes in monitored metrics.

![CloudWatch EC2 CPU utilization metrics](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/cloudwatch-metrics.png)

### 2. AWS CloudTrail

AWS CloudTrail records activities performed in an AWS account, including management events generated through the AWS Management Console, CLI, and APIs.

The project uses a multi-Region trail named kltn-trail. The trail delivers logs to an S3 bucket and uses AWS KMS encryption.

To review CloudTrail:

1. Open the **CloudTrail** service.
2. Select **Trails**.
3. Find kltn-trail.
4. Review its multi-Region configuration.
5. Check the S3 destination and encryption settings.
6. Open **Event history** to review recorded management events.

CloudTrail provides an audit record that helps administrators investigate changes to AWS resources and account configurations.

![kltn-trail configuration in AWS CloudTrail](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/cloudtrail-trail.png)

### 3. AWS Config

AWS Config records resource configurations and evaluates resources against configuration rules.

The project enables AWS Config recording and uses configuration rules to review selected security requirements.

The configured rules include:

- cloudtrail-enabled

- ec2-instance-no-public-ip

- restricted-ssh

- vpc-default-security-group-closed

To review AWS Config:

1. Open the **AWS Config** service.
2. Review the recorder status.
3. Open **Resources** to inspect the recorded resource inventory.
4. Select **Rules**.
5. Review the evaluation results for each rule.
6. Check whether resources are compliant, noncompliant, or not evaluated.

The evaluation result of each rule must be considered separately. A rule with no evaluation result should not be described as compliant.

![AWS Config security rules and evaluation status](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/aws-config-rules.png)

### 4. Amazon EventBridge and SNS Notifications

Amazon EventBridge can detect selected AWS events and route them to configured targets.

The project uses an EventBridge rule named KLTN-SG-Change-Alert to detect ingress or egress rule changes for the EC2 Security Group.

The rule is associated with the notification workflow using Amazon SNS.

The SNS topic is named KLTN-Security-Alert, and its email subscription has been confirmed.

To review the notification configuration:

1. Open **Amazon EventBridge**.
2. Select **Rules**.
3. Find KLTN-SG-Change-Alert.
4. Review its event pattern and target configuration.
5. Open **Amazon SNS**.
6. Select KLTN-Security-Alert.
7. Review the topic and confirmed email subscription.

CloudWatch metrics can also be used to review EventBridge rule activity, including matched events and invocations.

![Enabled EventBridge rule for Security Group change notifications](/images/4-Workshop/4.7-Centralized%20Monitoring%20and%20Logging/eventbridge-rule.png)

### 5. Security Monitoring Benefits

The monitoring and logging services provide several benefits:

- CloudWatch helps observe resource performance and monitoring metrics.

- CloudTrail records account activities for auditing and investigation.

- AWS Config tracks resource configurations and evaluates selected security rules.

- EventBridge detects configured security-related events.

- SNS delivers notifications to subscribed email addresses.

Together, these services improve visibility into infrastructure activities and help administrators review security-related changes.

### 6. Conclusion

This section demonstrates the use of AWS monitoring, logging, and notification services.

CloudWatch, CloudTrail, and AWS Config provide resource monitoring, activity recording, and configuration evaluation. EventBridge and SNS extend this capability by supporting notifications for selected Security Group changes.

