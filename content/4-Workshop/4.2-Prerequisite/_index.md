---
title: "Prerequisites"
date: 2026-10-29
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

### 1. Overview of the Deployment Environment

Before implementing the AWS infrastructure security environment, several basic requirements must be prepared, including an AWS account, an administration computer, network planning, and access permissions.

The project is deployed in the Asia Pacific (Singapore) Region (ap-southeast-1). The environment uses Amazon VPC, EC2, an Application Load Balancer, AWS WAF, IAM, AWS Systems Manager, and monitoring and logging services.

![AWS Management Console in the Singapore Region](/images/4-Workshop/4.2-Prerequisites/aws-region.png)

### 2. Required Components

- **AWS Account:** An AWS account is required to access the AWS Management Console and deploy cloud resources.

- **AWS Management Console:** Used to configure and manage AWS services.

- **Authorized IAM Identity:** An IAM user or role with sufficient permissions is required to create and manage the resources used in the project.

- **Amazon VPC:** Provides an isolated network environment for the cloud infrastructure.

- **Amazon EC2:** Hosts the Nginx web server inside a private subnet.

- **VPC Endpoints:** Provide private connectivity between the VPC and supported AWS services, including Systems Manager.

- **Application Load Balancer and AWS WAF:** Provide web traffic distribution and protection.

- **Monitoring and Logging Services:** CloudWatch, CloudTrail, AWS Config, EventBridge, and SNS support monitoring, auditing, configuration review, and notifications.

- **Administration Computer:** A computer with a modern web browser and terminal is required to access the AWS Console and perform verification tasks.

### 3. Prerequisites Before Deployment

Before starting the workshop, ensure that:

1. An AWS account is available and can access the AWS Management Console.
2. The account has sufficient permissions to configure the required AWS services.
3. A stable Internet connection and a modern web browser are available.
4. The selected AWS Region is Asia Pacific (Singapore) (ap-southeast-1).
5. The VPC CIDR range and subnet address ranges have been planned without overlapping.
6. Basic knowledge of IP addressing, subnetting, routing, and network security is recommended.
7. AWS pricing and resource usage have been reviewed to avoid unnecessary costs.

### 4. Expected Outcome

After completing this preparation stage, the AWS account, working region, access permissions, and network plan are ready for the infrastructure deployment.

These requirements provide the foundation for creating the VPC environment, deploying the private EC2 web server, configuring secure access, protecting web traffic, and monitoring infrastructure activities.

