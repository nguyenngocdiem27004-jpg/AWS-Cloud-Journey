---
title: "Design and Deployment of AWS Network Infrastructure"
date: 2026-10-30
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

#### Overview of AWS Network Infrastructure

Amazon Virtual Private Cloud (Amazon VPC) provides a logically isolated network environment in AWS. It allows administrators to configure IP address ranges, subnets, route tables, and network connectivity for cloud resources.

In this project, the AWS network infrastructure is deployed in the Asia Pacific (Singapore) Region (`ap-southeast-1`). The VPC is divided into public and private subnets to separate resources according to their roles and access requirements.

The main network components include Amazon VPC, public and private subnets, an Internet Gateway, a NAT Gateway, and route tables. These components provide network connectivity while helping control access to resources inside the VPC.

#### Deployment Objectives

- Create and configure an Amazon VPC with an appropriate IP address range.
- Divide the VPC into public and private subnets across Availability Zones.
- Attach an Internet Gateway to provide Internet connectivity for public subnets.
- Configure a NAT Gateway to allow resources in private subnets to access the Internet when required.
- Configure route tables and subnet associations to control network traffic.
- Prepare the network environment for deploying Amazon EC2 and Amazon RDS resources.

#### IP Addressing Design

The project uses the private IP address range `10.0.0.0/16` for the VPC. This range provides sufficient address space for multiple public and private subnets.

| Component | Resource Name | IP Range / Configuration |
|---|---|---|
| Amazon VPC | KLTN-VPC | `10.0.0.0/16` |
| Public Subnets | Configured in KLTN-VPC | Refer to the actual subnet CIDR ranges in AWS Console |
| Private Subnet 2 | KLTN-Private-Subnet-2 | `10.0.4.0/24` |
| Internet Gateway | Attached to KLTN-VPC | Provides Internet connectivity for public subnets |
| NAT Gateway | Configured in a public subnet | Allows outbound Internet access from private subnets |
| Private Route Table | KLTN-Private-RT | Routes traffic for associated private subnets |

The CIDR ranges and Availability Zones of the remaining subnets should be checked in the Amazon VPC console to ensure that the documentation matches the deployed environment.

#### Deploying Amazon VPC

Amazon VPC is a logically isolated virtual network that allows administrators to control IP address ranges, subnets, routing, and network connectivity.

The project uses an existing VPC named `KLTN-VPC`.

To review the VPC configuration:

1. Access the AWS Management Console.
2. Open the **Amazon VPC** service.
3. Select **Your VPCs**.
4. Find and select `KLTN-VPC`.
5. Review its IPv4 CIDR block and other network settings.
6. Verify that the VPC is available and that its configuration matches the project design.

The VPC uses the IPv4 CIDR block `10.0.0.0/16`.

#### Creating and Configuring Subnets

Subnets divide a VPC into smaller network segments. Public subnets are used for resources that require a route to the Internet Gateway, while private subnets are used for resources that should not be directly accessible from the Internet.

The project uses two public subnets and two private subnets.

To review the subnet configuration:

1. In the Amazon VPC console, select **Subnets**.
2. Filter the subnet list by the VPC `KLTN-VPC`.
3. Review the names, IPv4 CIDR blocks, and Availability Zones of the four subnets.
4. Verify that the public and private subnets use separate network ranges.
5. Check the route table association of each subnet.
6. For public subnets that need to assign public IPv4 addresses automatically, verify the **Enable auto-assign public IPv4 address** setting.

A private subnet used by the project is named `KLTN-Private-Subnet-2`, with the CIDR block `10.0.4.0/24`.

#### Creating and Attaching an Internet Gateway

An Internet Gateway allows resources in a VPC to communicate with the Internet when the appropriate routing and security configurations are in place.

To review the Internet Gateway configuration:

1. In the Amazon VPC console, select **Internet gateways**.
2. Find the Internet Gateway attached to `KLTN-VPC`.
3. Select the Internet Gateway and review its details.
4. Verify that its state indicates that it is attached to the correct VPC.

The Internet Gateway is used by the public route table to provide a route to the Internet.

#### Configuring the NAT Gateway

A NAT Gateway allows resources in private subnets to initiate connections to the Internet without allowing unsolicited inbound connections from the Internet.

To review the NAT Gateway configuration:

1. In the Amazon VPC console, select **NAT gateways**.
2. Find the NAT Gateway configured for the project.
3. Verify that its state is **Available**.
4. Check that it is deployed in a public subnet.
5. Review the private route table to confirm that the default route points to the NAT Gateway.

The NAT Gateway provides outbound Internet connectivity for resources in private subnets when required.

#### Configuring Route Tables

A route table determines where network traffic is directed. Public and private subnets use route tables with different routing configurations.

For the public route table:

1. In the Amazon VPC console, select **Route tables**.
2. Select the route table associated with the public subnets.
3. Open the **Routes** tab.
4. Verify that the route `0.0.0.0/0` points to the Internet Gateway.
5. Open **Subnet associations** and verify the associated public subnets.

For the private route table:

1. Select `KLTN-Private-RT`.
2. Open the **Routes** tab.
3. Verify that the route `0.0.0.0/0` points to the NAT Gateway, if private subnet Internet access is required.
4. Open **Subnet associations**.
5. Verify that the intended private subnets are associated with this route table.

The route table configuration separates public and private network traffic and supports the intended access requirements of the project.

#### Verifying the Deployment

After reviewing the network configuration, verify the following:

- The VPC `KLTN-VPC` uses the CIDR block `10.0.0.0/16`.
- The VPC contains two public subnets and two private subnets.
- The Internet Gateway is attached to the correct VPC.
- The public route table contains a default route pointing to the Internet Gateway.
- The NAT Gateway is available in a public subnet.
- The private route table uses the NAT Gateway as its default route when outbound Internet access is required.
- The subnet associations match the intended network design.

#### Expected Results

After completing this section, the AWS network infrastructure provides a foundation for deploying and connecting cloud resources. Public and private subnets help separate resources according to their access requirements, while Internet Gateway, NAT Gateway, and route tables control network connectivity.

The next section focuses on Amazon EC2 and Security Groups, which are used to deploy the web server and control network access to the instance.