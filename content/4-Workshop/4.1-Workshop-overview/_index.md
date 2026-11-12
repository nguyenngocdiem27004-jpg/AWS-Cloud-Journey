---
title: "Introduction"
date: 2026-10-29
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

#### Introduction to AWS Infrastructure Security

- **AWS Cloud Infrastructure** provides an environment for deploying and managing computing, networking, and database resources. AWS offers various services that help organizations build and manage cloud environments.

- **Network Security** is an important part of cloud infrastructure protection. Amazon VPC, subnets, route tables, Security Groups, and Network Access Control Lists (NACLs) help organize network resources and control access to them.

- **Identity and Access Management** helps manage permissions for AWS resources. AWS Identity and Access Management (IAM) supports access control and the implementation of the principle of least privilege.

- **Monitoring and Configuration Management** help administrators observe resource information, review account activities, and evaluate infrastructure configurations. AWS provides services such as Amazon CloudWatch, AWS CloudTrail, and AWS Config to support these tasks.

#### Workshop Overview

This workshop introduces an AWS infrastructure environment and the security configurations implemented as part of the project **"Research and Implementation of Infrastructure Security on AWS."**

The environment includes the following main components:

- **"AWS Network Infrastructure"** uses Amazon VPC to organize the cloud network with public and private subnets, an Internet Gateway, a NAT Gateway, and route tables.

- **"Compute and Database Environment"** uses Amazon EC2 to deploy a web server and Amazon RDS to provide a managed MySQL database. Network access between these resources is controlled through security configurations.

- **"Access Control and Network Security"** uses IAM roles and policies to manage permissions, while Security Groups control network traffic between the Application Load Balancer, EC2 instance, and RDS database.

- **"Application Access and Protection"** uses an Application Load Balancer (ALB) to provide access to the web server. AWS WAF is associated with the ALB to inspect and filter web requests.

- **"Monitoring and Configuration Review"** introduces Amazon CloudWatch, AWS CloudTrail, and AWS Config for observing resource information, reviewing account activities, and checking resource configurations.

Through this workshop, you will explore the architecture of an AWS environment, understand how its services work together, and review the security configurations and practical tests performed during the project.