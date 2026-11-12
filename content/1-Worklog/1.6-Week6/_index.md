---
title: "Worklog Week 6"
date: 2026-09-19
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Learn about Amazon RDS and its role in providing managed database services for the AWS infrastructure.
- Create and configure an Amazon RDS database instance within the AWS VPC.
- Understand how to configure database access through Security Groups.
- Verify network connectivity between the EC2 instance and the RDS database.
- Learn about Application Load Balancer (ALB) and its role in distributing incoming application traffic.
- Prepare the environment for web server deployment and load balancing.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Study Amazon RDS and the benefits of using a managed relational database service.<br>- Learn about database engines, instance configurations, and storage options.<br>- Review the requirements for deploying an RDS database within private subnets.<br>- Study the role of DB Subnet Groups in database network configuration. | 19/09/2026 | 19/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Create an RDS DB Subnet Group using the appropriate private subnets.<br>- Configure the RDS database instance with a suitable database engine and instance configuration.<br>- Configure the database Security Group to restrict inbound access.<br>- Check the database instance status after creation. | 20/09/2026 | 21/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Review the Security Group configuration for the EC2 instance and RDS database.<br>- Configure the RDS Security Group to allow database traffic from the EC2 Security Group on the required port.<br>- Check network connectivity between EC2 and RDS.<br>- Review the database endpoint and connection parameters. | 22/09/2026 | 23/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Study Application Load Balancer and its role in distributing incoming traffic.<br>- Learn about listeners, target groups, and health checks.<br>- Review the network and Security Group requirements for connecting an ALB to EC2.<br>- Summarize the RDS connectivity test results and prepare for web server deployment and load balancing in the following week. | 24/09/2026 | 25/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Week 6 Results:

- Understood the basic concepts of Amazon RDS and its role in providing managed database services.
- Learned how to configure a DB Subnet Group using private subnets.
- Created and configured an RDS database instance within the AWS VPC.
- Configured Security Groups to control database access and restrict connections to authorized resources.
- Verified network connectivity between the EC2 instance and the RDS database through the required database port.
- Understood how database endpoints and connection parameters are used when accessing an RDS instance.
- Learned the basic concepts of Application Load Balancer, listeners, target groups, and health checks.
- Prepared the database and network environment for the next stage of web server deployment and load balancing.