---
title: "Worklog Week 3"
date: 2026-08-24
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Deploy the basic network infrastructure on AWS based on the architecture and IP addressing plan developed in Week 2.
- Create and configure an Amazon VPC with a suitable CIDR range for the AWS infrastructure security project.
- Create public and private subnets and understand how to allocate network resources within the VPC.
- Configure an Internet Gateway and Route Tables to control network traffic paths.
- Verify the network configuration to prepare for deploying Amazon EC2 and configuring security controls in the following weeks.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Access the AWS Management Console and open the Amazon VPC service.<br>- Create a VPC for the infrastructure security project.<br>- Configure the VPC IPv4 CIDR range according to the previously developed plan.<br>- Verify the VPC information and status after creation. | 24/08/2026 | 24/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Create public and private subnets within the VPC according to the IP addressing plan.<br>- Determine the CIDR range and Availability Zone for each subnet.<br>- Understand the differences between public and private subnets.<br>- Configure automatic public IPv4 address assignment for public subnets when required. | 25/08/2026 | 26/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Create an Internet Gateway and attach it to the VPC.<br>- Create and configure Route Tables for the public subnet.<br>- Add the default route `0.0.0.0/0` pointing to the Internet Gateway.<br>- Associate the Route Table with the corresponding subnet and verify the configured routes. | 27/08/2026 | 27/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Review the configuration of the VPC, subnets, Internet Gateway, and Route Tables.<br>- Check the CIDR ranges, subnet associations, and routing entries.<br>- Compare the actual configuration with the architecture diagram and IP addressing plan.<br>- Summarize the implementation results as preparation for Week 4. | 28/08/2026 | 28/08/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Week 3 Results:

- Created and configured an Amazon VPC for the AWS infrastructure security project.
- Configured the VPC IPv4 CIDR range according to the network design plan.
- Created public and private subnets to organize network resources and separate different infrastructure components.
- Understood that public and private subnets are distinguished by their routing configuration rather than their names alone.
- Created an Internet Gateway and attached it to the VPC to provide Internet connectivity for eligible resources.
- Created and configured Route Tables with the necessary routing entries:
  - The local route enables communication between resources within the VPC according to the network configuration.
  - The default route `0.0.0.0/0` points to the Internet Gateway for Internet-bound traffic from the public subnet.
- Associated Route Tables with the corresponding subnets and verified the routing entries.
- Compared the actual AWS network configuration with the architecture diagram and IP addressing plan developed in Week 2.
- Completed the basic VPC network infrastructure, providing a foundation for deploying Amazon EC2 and implementing security controls in the following weeks.