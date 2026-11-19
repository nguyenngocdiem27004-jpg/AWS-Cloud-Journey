---
title: "Security Testing and Infrastructure Review"
date: 2026-10-30
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

#### Overview

This final section reviews the AWS infrastructure and summarizes the security verification activities performed during the project.

The testing focuses on private EC2 access, web server availability, ALB traffic forwarding, AWS WAF filtering, Security Group configuration, and monitoring and logging services.

The purpose is to verify the implemented security controls, identify potential configuration issues, and review resource usage.

### 1. Review the AWS Infrastructure

The main resources reviewed during the final verification include:

| Component | Resource / Configuration |
|---|---|
| VPC | KLTN-VPC |
| VPC CIDR | 10.0.0.0/16 |
| Private Subnets | 10.0.2.0/24 and 10.0.4.0/24 |
| EC2 Instance | KLTN-Web-Server |
| EC2 Private IP | 10.0.2.35 |
| EC2 Access | AWS Systems Manager Session Manager |
| Web Server | Nginx |
| Load Balancer | KLTN-ALB |
| Web ACL | KLTN-WebACL |
| Monitoring | CloudWatch, CloudTrail, AWS Config |
| Notifications | EventBridge and SNS |

The review confirms the main components used in the current infrastructure. RDS and NAT Gateway are not included as active resources in this final configuration.

![Private EC2 instance details showing no public IPv4 address](/images/4-Workshop/4.8-System%20Testing%20and%20Cleanup/test-private-ec2.png)

### 2. EC2 and Web Server Verification

The EC2 instance is reviewed to confirm that it is running in the private subnet and does not have a public IPv4 address.

The following checks are performed:

- Confirm that KLTN-Web-Server is running.

- Check that the instance status checks have passed.

- Verify the private IP address.

- Confirm that Session Manager can establish a connection.

- Check that the Nginx service is running.

The local web server response can be checked from the EC2 terminal:

```bash
curl -I http://localhost
```

A successful HTTP response confirms that Nginx is responding locally.

### 3. Application Load Balancer Verification

The Application Load Balancer is checked to confirm that it can forward web requests to the EC2 target.

The verification includes:

- Reviewing the ALB listener configuration.

- Checking the associated target group.

- Confirming that the registered target is healthy.

- Sending a normal HTTP request to the ALB DNS name.

A successful response with HTTP 200 confirms that the web service is accessible through the ALB.

![Normal web request verification](/images/4-Workshop/4.8-System%20Testing%20and%20Cleanup/test-normal.png)

### 4. AWS WAF Security Testing

AWS WAF is tested using normal and potentially malicious HTTP request patterns.

The observed results are summarized below:

| Test Case | Result |
|---|---|
| Normal HTTP request | HTTP 200 |
| SQL injection pattern before WAF protection | HTTP 200 |
| SQL injection pattern after WAF protection | HTTP 403 |
| XSS pattern before WAF protection | HTTP 200 |
| XSS pattern after WAF protection | HTTP 403 |
| Path traversal-style request | HTTP 400 |

The results demonstrate that the configured WAF protection blocks the tested SQL injection and XSS requests while normal web access remains available.

The path traversal-style request was rejected with HTTP 400. The response alone does not identify which AWS component rejected the request.

![SQL injection and XSS verification after WAF protection](/images/4-Workshop/4.8-System%20Testing%20and%20Cleanup/test-sqli-xss.png)

### 5. Network and Access Control Review

The network and access control configurations are reviewed to ensure that private resources are not unnecessarily exposed.

The review includes:

- Checking that the EC2 instance has no public IPv4 address.

- Reviewing the EC2 Security Group rules.

- Confirming that administrative access is provided through Session Manager.

- Reviewing the IAM role assigned to EC2.

- Checking the availability of the Systems Manager VPC Endpoints.

- Reviewing the public and private route table configurations.

These checks help verify that access to the private server is controlled through the intended network and identity configurations.

### 6. Monitoring and Configuration Review

The monitoring and auditing services are reviewed to confirm that infrastructure activities and configurations can be inspected.

**Amazon CloudWatch**

Review available EC2 metrics and EventBridge activity metrics, including matched events and invocations.

**AWS CloudTrail**

Review the kltn-trail configuration and event history to identify recorded account activities.

**AWS Config**

Review the recorder status, resource inventory, and evaluation results of the configured security rules.

The configured rules include:

- cloudtrail-enabled

- ec2-instance-no-public-ip

- restricted-ssh

- vpc-default-security-group-closed

The compliance status must be based on the actual evaluation results shown in AWS Config.

**EventBridge and SNS**

Review the KLTN-SG-Change-Alert rule and the KLTN-Security-Alert SNS topic to verify the security notification configuration.

### 7. AWS Resource Usage and Cost Review

AWS resources should be reviewed before and after testing to avoid unnecessary charges.

The following services and resources should be checked:

- **EC2:** Review running instances and their instance types.

- **EBS:** Review attached volumes and unused storage.

- **Elastic Load Balancing:** Review the Application Load Balancer and its usage.

- **VPC Endpoints:** Review the configured endpoints and their associated costs.

- **AWS WAF:** Review the Web ACL and usage charges.

- **CloudWatch:** Review metrics, logs, and additional monitoring resources.

- **CloudTrail and AWS Config:** Review the enabled recording and storage configurations.

- **SNS:** Review the notification topic and subscriptions.

Billing and Cost Management can be used to review service-level charges and estimated spending.

Resources that are no longer required for testing should be stopped or deleted where appropriate. Logging and audit resources should be retained according to the project's documentation requirements.

### 8. Final Verification Summary

| Verification Item | Observed Result |
|---|---|
| VPC KLTN-VPC | Configured |
| Private Subnets | Two configured |
| EC2 KLTN-Web-Server | Running |
| EC2 public IPv4 | Not assigned |
| Session Manager | Connection successful |
| Nginx | Running |
| Application Load Balancer | Deployed; target health verified |
| AWS WAF | Associated with ALB |
| SQL injection test after WAF | HTTP 403 |
| XSS test after WAF | HTTP 403 |
| CloudTrail | Trail configured |
| AWS Config | Recording enabled |
| EventBridge | Security Group change rule enabled |
| SNS | Email subscription confirmed |

### 9. Conclusion

The final verification demonstrates the operation of the main AWS infrastructure components and the security controls implemented in the project.

The EC2 web server operates in a private subnet and can be managed through Systems Manager Session Manager without requiring a public IP address or inbound SSH access.

The Application Load Balancer provides access to the web server, while AWS WAF blocks the tested SQL injection and XSS requests. CloudWatch, CloudTrail, AWS Config, EventBridge, and SNS provide additional monitoring, auditing, configuration review, and notification capabilities.

The project therefore demonstrates how AWS networking, identity management, web protection, and monitoring services can be combined to improve infrastructure security while keeping resource usage under review.

