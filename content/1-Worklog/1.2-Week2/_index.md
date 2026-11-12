
---
title: "Worklog Week 2"
date: 2026-08-17
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

- Study the requirements for designing and implementing a secure AWS infrastructure.
- Identify a suitable AWS architecture for deploying and protecting cloud resources.
- Plan the network structure using Amazon VPC, Public Subnets, and Private Subnets.
- Plan IP address ranges and subnet allocation to organize AWS resources and avoid overlapping networks.
- Identify the security components required for the project, including Security Groups, Network ACLs, IAM, and network routing.
- Prepare an initial architecture diagram and implementation plan for the following weeks.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Analyze the requirements of the AWS infrastructure security project.<br>- Identify the main components of the system, including VPC, subnets, EC2 instances, databases, and security services.<br>- Determine the network access and protection requirements for AWS resources.<br>- Draft an initial architecture for the secure AWS environment. | 17/08/2026 | 17/08/2026 | [AWS Documentation](https://docs.aws.amazon.com/) |
| 3 | - Study the network components used in Amazon VPC.<br>- Analyze the roles of Public Subnets, Private Subnets, Route Tables, Internet Gateway, and NAT Gateway.<br>- Understand how network segmentation helps isolate and protect cloud resources.<br>- Identify suitable network paths for public-facing and internal resources. | 18/08/2026 | 19/08/2026 | [Amazon VPC Documentation](https://docs.aws.amazon.com/vpc/) |
| 4 | - Develop an IP addressing plan for the AWS network.<br>- Determine the CIDR range for the VPC and its subnets.<br>- Plan the placement of EC2 instances and database resources in appropriate subnets.<br>- Review Security Groups and Network ACLs to define network access control requirements. | 20/08/2026 | 20/08/2026 | [Amazon VPC Documentation](https://docs.aws.amazon.com/vpc/) |
| 5 | - Finalize the initial AWS infrastructure architecture diagram.<br>- Identify the security services required for implementation, including IAM, AWS WAF, CloudTrail, CloudWatch, and AWS Config.<br>- Prepare the network configuration plan and security requirements for the implementation phase.<br>- Review the architecture before deploying AWS resources in the following weeks. | 21/08/2026 | 21/08/2026 | [AWS Security Documentation](https://docs.aws.amazon.com/security/) |

### Week 2 Results:

- Identified the objectives and requirements of the AWS infrastructure security project.
- Developed an initial architecture design for deploying and protecting resources on AWS.
- Gained a better understanding of the roles of AWS networking components:
  - **Amazon VPC:** Provides an isolated virtual network environment for AWS resources.
  - **Public Subnet:** Hosts resources that require a route to the Internet through an Internet Gateway.
  - **Private Subnet:** Hosts internal resources that should not be directly accessible from the Internet.
  - **Route Table:** Controls the routing paths of network traffic within the VPC.
  - **Internet Gateway:** Enables communication between a VPC and the Internet for eligible resources.
  - **NAT Gateway:** Allows resources in private subnets to initiate outbound Internet connections without accepting unsolicited inbound connections.
- Prepared an initial IP addressing plan for the VPC and its subnets.
- Understood the importance of network segmentation and controlling access to AWS resources.
- Identified the roles of Security Groups and Network ACLs in filtering network traffic.
- Explored security and monitoring services required for the project, including IAM, AWS WAF, CloudTrail, CloudWatch, and AWS Config.
- Prepared the initial architecture and configuration requirements for implementing the secure AWS infrastructure in the following weeks.
