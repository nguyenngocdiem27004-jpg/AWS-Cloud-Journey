---
title: "Prerequisites"
date: 2026-10-29
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

#### Overview of the Deployment Environment

To implement an AWS infrastructure security system, we need to prepare an AWS account, a computer for administration, an Internet connection, and a basic network design.

The project uses Amazon Web Services (AWS) to build and manage the cloud infrastructure. The deployment environment is based on the Singapore Region (`ap-southeast-1`), where the network, computing, database, and security resources are configured.

The infrastructure includes an Amazon VPC with public and private subnets, an Internet Gateway, a NAT Gateway, route tables, an EC2 web server, an RDS MySQL database, and an Application Load Balancer. Additional AWS services are used to manage access, protect web traffic, and review infrastructure activities.

#### Required Components

- **Amazon Web Services (AWS) Account:** Required to access the AWS Management Console and create or manage cloud resources.

- **AWS Management Console:** Used to configure and manage services such as Amazon VPC, EC2, RDS, IAM, Elastic Load Balancing, and AWS WAF.

- **IAM User and Permissions:** Used to access AWS services and perform the operations required for the project. Appropriate permissions must be available for the resources being configured.

- **Amazon VPC:** Used to create the cloud network environment, including public and private subnets, an Internet Gateway, a NAT Gateway, and route tables.

- **Amazon EC2:** Used to deploy the web server and provide a computing environment for testing network access.

- **Amazon RDS:** Used to deploy and manage a MySQL database within the AWS environment.

- **Application Load Balancer (ALB) and AWS WAF:** Used to provide access to the web server and apply web traffic protection rules.

- **Administration Computer:** Used to access the AWS Management Console, configure resources, connect to the EC2 instance, and perform testing through a web browser or terminal.

#### Prerequisites Before Deployment

Before starting the workshop, ensure that the following requirements are met:

1. An AWS account has been created and can access the AWS Management Console.
2. An IAM user or another authorized identity has the permissions required to configure the necessary AWS services.
3. A computer with a modern web browser and a stable Internet connection is available.
4. The AWS Region is selected as Asia Pacific (Singapore) (`ap-southeast-1`).
5. An IP addressing plan has been prepared for the VPC and its public and private subnets. The selected CIDR ranges must not overlap.
6. Basic knowledge of cloud computing, IP addressing, subnetting, and network access control is recommended.
7. AWS pricing and resource usage should be reviewed before deployment to avoid unnecessary costs.

#### Expected Outcome

After completing the preparation stage, we will have an accessible AWS account, an appropriate working region, the necessary permissions, and an initial IP addressing plan.

These preparations provide the foundation for building the VPC network, deploying EC2 and RDS resources, configuring access control, protecting web traffic, and reviewing infrastructure security in the following sections.