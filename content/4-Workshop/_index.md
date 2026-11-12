---
title: "Workshop"
date: 2026-10-27
weight: 5
chapter: false
pre: " <b> 4. </b> "
---

# Research and Implementation of Infrastructure Security on AWS

#### Overview

In this workshop, we will explore the design and implementation of a secure cloud infrastructure using Amazon Web Services (AWS).

The project focuses on building an AWS network environment with Amazon VPC, public and private subnets, Internet Gateway, NAT Gateway, and route tables. Amazon EC2 is deployed as the web server, while Amazon RDS provides database services within the cloud environment.

To improve infrastructure security, the project applies AWS Identity and Access Management (IAM), Security Groups, Application Load Balancer (ALB), and AWS Web Application Firewall (WAF). In addition, Amazon CloudWatch, AWS CloudTrail, and AWS Config are used to review resource performance, account activities, and resource configurations.

Through this workshop, we will explore the AWS network architecture, deploy and configure cloud resources, control network access, verify connectivity between EC2 and RDS, and review the monitoring and security capabilities provided by AWS services.

#### Objectives

- **AWS Cloud Architecture:** Understand and design a cloud infrastructure using Amazon VPC and related networking components.
- **AWS Network Infrastructure:** Configure VPC, public and private subnets, Internet Gateway, NAT Gateway, and route tables.
- **Amazon EC2 Deployment:** Deploy a web server and configure secure access using IAM roles and Systems Manager Session Manager.
- **Database Connectivity:** Configure network access between Amazon EC2 and Amazon RDS using Security Groups.
- **Infrastructure Security:** Apply IAM permissions, Security Groups, Application Load Balancer, and AWS WAF.
- **Monitoring and Logging:** Explore Amazon CloudWatch, AWS CloudTrail, and AWS Config.
- **Security Review:** Verify network connectivity, review access control rules, and examine the security configuration of AWS resources.

#### Contents

1. [Introduction](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequisite/)
3. [Design and Deployment of AWS Network Infrastructure](5.3-AWS-Network-Infrastructure/)
4. [Deployment of Amazon EC2 and Security Group Configuration](5.4-EC2-Security-Groups/)
5. [Connectivity Between Amazon EC2 and Amazon RDS](5.5-Site-to-Site-VPN/)
6. [AWS WAF Configuration and Web Traffic Filtering](5.6-VPN-Routing-Failover/)
7. [AWS Infrastructure Monitoring and Logging](5.7-Centralized-Monitoring/)
8. [Security Testing and Infrastructure Review](5.8-System-Testing-Cleanup/)