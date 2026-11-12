---
title: "Worklog Week 5"
date: 2026-09-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- Review and complete the AWS VPC network architecture implemented in previous weeks.
- Understand the role of public and private subnets in separating AWS infrastructure resources.
- Learn about NAT Gateway and its role in providing outbound Internet access for resources in private subnets.
- Configure Route Tables to control traffic between public and private subnets and external networks.
- Review Security Group rules to control communication between EC2 instances and other AWS resources.
- Verify network connectivity and prepare the infrastructure for deploying additional security services.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Review the existing VPC architecture and subnet configuration.<br>- Study the differences between public and private subnets.<br>- Review the role of Internet Gateway and NAT Gateway in the AWS network architecture.<br>- Identify the network traffic requirements for resources deployed in each subnet. | 12/09/2026 | 12/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Create and configure a NAT Gateway in a public subnet.<br>- Allocate an Elastic IP address for the NAT Gateway.<br>- Review the private subnet Route Table configuration.<br>- Add a default route `0.0.0.0/0` pointing to the NAT Gateway when required. | 13/09/2026 | 14/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Review the Route Tables associated with public and private subnets.<br>- Verify the routing paths through the Internet Gateway and NAT Gateway.<br>- Review Security Group rules for the EC2 instance and other related resources.<br>- Understand how Security Groups control communication between different infrastructure components. | 15/09/2026 | 16/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Check the VPC, subnet, NAT Gateway, and Route Table configurations.<br>- Verify the network connectivity required by the EC2 instance.<br>- Review the network separation between public-facing and private resources.<br>- Summarize the network implementation results and prepare for the next stage of infrastructure security deployment. | 17/09/2026 | 18/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Week 5 Results:

- Reviewed the AWS VPC architecture and the network configuration implemented in previous weeks.
- Understood the roles of public and private subnets in separating infrastructure resources.
- Learned about NAT Gateway and its function in allowing resources in private subnets to access the Internet without requiring direct inbound Internet connectivity.
- Configured the NAT Gateway and associated an Elastic IP address with it.
- Configured the private subnet Route Table with the appropriate routing entry pointing to the NAT Gateway.
- Reviewed the Route Tables of public and private subnets and verified their routing configurations.
- Reviewed Security Group rules to control network traffic between EC2 and other AWS resources.
- Improved the understanding of network isolation and traffic control within the AWS VPC.
- Completed the basic network configuration required for the next stages of deploying and securing AWS infrastructure.