---
title: "Worklog Week 4"
date: 2026-09-05
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- Learn about Amazon EC2 and its role in deploying virtual servers for the AWS infrastructure security project.
- Understand EC2 instance types, Amazon Machine Images (AMIs), and Amazon EBS storage.
- Launch and configure an EC2 instance within the VPC created in Week 3.
- Configure Security Groups to control inbound and outbound traffic and protect the EC2 instance.
- Learn how to access and manage an EC2 instance using AWS Systems Manager Session Manager.
- Understand basic EC2 instance management operations to help control AWS costs.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Study Amazon EC2, instance types, AMIs, and EBS storage.<br>- Learn how to select a suitable instance type and operating system for the project.<br>- Review the basic configuration options required when launching an EC2 instance. | 05/09/2026 | 05/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Launch an EC2 instance in the VPC created in Week 3.<br>- Select the AMI, instance type, subnet, and storage capacity.<br>- Configure the instance network settings and assign an appropriate Security Group.<br>- Check the instance status and assigned IP address. | 06/09/2026 | 07/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Create and configure a Security Group for the EC2 instance.<br>- Review inbound rules and allow only the necessary traffic.<br>- Configure HTTP access on TCP port 80 when required for the web server.<br>- Review outbound rules and apply the principle of least privilege.<br>- Learn how Security Groups help protect cloud resources. | 08/09/2026 | 08/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Learn how to configure an IAM Role for EC2 to use AWS Systems Manager.<br>- Connect to the EC2 instance using Systems Manager Session Manager.<br>- Inspect the operating system, network configuration, and basic system resources.<br>- Verify the instance status and review its access configuration.<br>- Learn how to stop and start the EC2 instance to help manage AWS costs. | 09/09/2026 | 09/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Week 4 Results:

- Understood the basic concepts of Amazon EC2, instance types, AMIs, and EBS storage.
- Learned how to select an appropriate EC2 configuration for the AWS infrastructure security project.
- Launched an EC2 instance within the VPC and learned how to check its status and IP address.
- Created and configured a Security Group to control inbound and outbound network traffic.
- Understood how to restrict network access by allowing only the necessary traffic through Security Group rules.
- Learned how to configure an IAM Role and use AWS Systems Manager Session Manager to access the EC2 instance without relying on direct SSH access.
- Performed basic system and network checks on the EC2 instance.
- Understood basic EC2 management operations, including stopping and starting instances to help control AWS costs.
- Established the compute environment for the next stages of the project, including deploying a web server and implementing additional infrastructure security controls.