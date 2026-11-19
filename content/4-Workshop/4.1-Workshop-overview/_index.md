---
title: "Introduction"
date: 2026-10-29
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

### 1. Introduction to AWS Infrastructure Security

AWS infrastructure security involves protecting cloud resources, controlling network access, managing permissions, and monitoring activities within an AWS environment.

The main security areas covered in this project include:

- **Network Security:** Amazon Virtual Private Cloud (VPC), subnets, route tables, Internet Gateway, Security Groups, and VPC Endpoints help organize network resources and control communication between components.

- **Identity and Access Management:** AWS Identity and Access Management (IAM) provides mechanisms for managing permissions. IAM roles and policies are used to grant the required access while following the principle of least privilege.

- **Secure Instance Administration:** AWS Systems Manager (SSM) Session Manager provides a way to access and manage EC2 instances without requiring a public IP address or direct SSH access.

- **Web Application Protection:** Application Load Balancer (ALB) distributes incoming web traffic to the application server, while AWS Web Application Firewall (WAF) inspects and filters web requests based on configured rules.

- **Monitoring and Auditing:** Amazon CloudWatch, AWS CloudTrail, and AWS Config help monitor resource activities, record account events, and review resource configurations.

### 2. Workshop Overview

This workshop presents the AWS infrastructure and security configurations implemented as part of the project **"Research and Implementation of Infrastructure Security on AWS."**

The environment is deployed in the Asia Pacific (Singapore) Region (ap-southeast-1) and consists of the following main components:

![AWS Infrastructure Architecture](/images/4-Workshop/4.1-Introduction/diagram.png)

- **AWS Network Infrastructure:** Amazon VPC provides an isolated network environment with public and private network segments, route tables, and an Internet Gateway. VPC Endpoints provide private connectivity to supported AWS services without requiring a NAT Gateway.

- **Compute Environment:** An Amazon EC2 instance named KLTN-Web-Server is deployed in a private subnet. The instance runs Nginx as the web server and does not have a public IPv4 address.

- **Access Control and Secure Administration:** IAM roles provide the permissions required by EC2 to communicate with AWS Systems Manager. Session Manager is used to access the instance without opening inbound SSH access.

- **Application Access and Protection:** An Application Load Balancer (ALB) provides the web access entry point to the EC2 web server. AWS WAF is associated with the ALB to inspect incoming requests and help block potentially malicious web traffic.

- **Monitoring, Logging, and Alerts:** Amazon CloudWatch is used to review resource metrics and monitoring information. AWS CloudTrail records account activities, while AWS Config tracks resource configurations and evaluates them against configuration rules. Amazon EventBridge and Amazon SNS support notifications for selected security-related events.

Through this workshop, you will explore the implemented AWS architecture, understand how the services work together, and review the security configurations and practical verification activities performed during the project.

### 3. Workshop Objectives

After completing this workshop, you should be able to:

- Understand the main components of an AWS network infrastructure.

- Organize cloud resources using Amazon VPC, subnets, and route tables.

- Deploy an EC2 web server in a private subnet.

- Apply IAM roles and Security Groups to control access.

- Use Systems Manager Session Manager for secure instance administration.

- Configure an Application Load Balancer and AWS WAF to protect web traffic.

- Review infrastructure activities and configurations using CloudWatch, CloudTrail, and AWS Config.

- Understand how EventBridge and SNS can support security event notifications.

- Perform basic security verification and review infrastructure resource usage.


