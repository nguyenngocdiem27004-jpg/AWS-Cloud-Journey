---
title: "Design and Deployment of AWS Network Infrastructure"
date: 2026-10-30
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### 1. Overview of AWS Network Infrastructure

Amazon Virtual Private Cloud (Amazon VPC) provides a logically isolated network environment in AWS. It allows administrators to define IP address ranges, create subnets, configure route tables, and control network connectivity.

In this project, the network infrastructure is deployed in the Asia Pacific (Singapore) Region (ap-southeast-1). The VPC provides the network boundary for the project. The EC2 web server is placed in a private subnet, while the route tables and Internet Gateway define the available network paths.

The environment uses VPC Endpoints to provide private connectivity to supported AWS services. This approach allows the private EC2 instance to communicate with Systems Manager without requiring a NAT Gateway or a public IP address.

#### Deployment Objectives

- Use an Amazon VPC to isolate the project network.

- Organize the project resources within the VPC and its private subnets.

- Configure route tables and subnet associations.

- Attach an Internet Gateway to the VPC.

- Configure VPC Endpoints for private access to supported AWS services.

- Prepare the network for the private EC2 web server and Application Load Balancer.

#### IP Addressing Design

The project uses the IPv4 CIDR block 10.0.0.0/16 for the VPC.

| Component | Resource Name | IP Range / Configuration |
|---|---|---|
| VPC | KLTN-VPC | 10.0.0.0/16 |
| Private Subnet 1 | KLTN-Private-Subnet | 10.0.2.0/24 |
| Private Subnet 2 | KLTN-Private-Subnet-2 | 10.0.4.0/24 |
| Private Route Table | KLTN-Private-RT | Associated with the private subnets |
| Public Route Table | KLTN-Public-RT | Used for public network routing |
| Internet Gateway | Attached to KLTN-VPC | Provides Internet connectivity for appropriately routed public resources |
| VPC Endpoints | SSM and SSMMessages endpoints | Private connectivity to Systems Manager |

### 2. Reviewing the Amazon VPC Configuration

The project uses an existing VPC named KLTN-VPC.

To review its configuration:

1. Open the AWS Management Console.
2. Navigate to **VPC**.
3. Select **Your VPCs**.
4. Find and select KLTN-VPC.
5. Review the IPv4 CIDR block.
6. Confirm that the VPC is in the available state.

The configured IPv4 CIDR block is 10.0.0.0/16.

![KLTN-VPC configuration and IPv4 CIDR](/images/4-Workshop/4.3-AWS%20Network%20Infrastructure/vpc-details.png)

### 3. Reviewing Subnets

Subnets divide a VPC into smaller network segments. They help separate resources according to their roles and access requirements.

To review the subnet configuration:

1. In the VPC console, select **Subnets**.
2. Filter the list by KLTN-VPC.
3. Review each subnet's name, IPv4 CIDR block, and Availability Zone.
4. Check the route table association of each subnet.
5. Confirm that the private subnets use the intended private route table.

The two private subnets used in the project are:

- KLTN-Private-Subnet: 10.0.2.0/24

- KLTN-Private-Subnet-2: 10.0.4.0/24

![The two private subnets in KLTN-VPC](/images/4-Workshop/4.3-AWS%20Network%20Infrastructure/subnets.png)

### 4. Internet Gateway and Route Tables

An Internet Gateway is attached to the VPC to support Internet connectivity for resources whose subnet routing and security rules permit it.

The project contains a public route table named KLTN-Public-RT and a private route table named KLTN-Private-RT.

To review route table settings:

1. Open **Route tables** in the VPC console.
2. Select KLTN-Public-RT and review its routes and subnet associations.
3. Select KLTN-Private-RT.
4. Open the **Routes** tab to review the configured destinations.
5. Open **Subnet associations** to confirm the associated private subnets.

The private route table is used to keep private subnet routing separate from public subnet routing. A NAT Gateway is not part of the current deployed environment.

![Route table subnet associations](/images/4-Workshop/4.3-AWS%20Network%20Infrastructure/route-tables.png)

### 5. Configuring VPC Endpoints

VPC Endpoints allow resources inside a VPC to connect to supported AWS services without requiring traffic to travel through a public Internet route.

The project uses Systems Manager-related VPC Endpoints to support private administration of the EC2 instance.

The configured endpoints include:

- KLTN-SSM-Endpoint

- KLTN-SSMMessages-Endpoint

To review the endpoint configuration:

1. Open the VPC console.
2. Select **Endpoints**.
3. Find the Systems Manager endpoints.
4. Review their service names, VPC association, subnet configuration, and endpoint security group.
5. Confirm that the endpoint state is **Available**.

The endpoint security group allows HTTPS traffic on TCP port 443 from the EC2 Security Group.

### 6. Verifying the Network Configuration

After reviewing the network environment, verify that:

- KLTN-VPC uses 10.0.0.0/16.

- Both private subnets exist with their intended CIDR ranges.

- The public and private route tables are available.

- The Internet Gateway is attached to the correct VPC.

- The SSM and SSMMessages VPC Endpoints are available.

- The private EC2 instance can use the configured endpoints for Systems Manager connectivity.

#### Expected Results

The VPC provides an isolated network environment for the project. The two private subnets, route tables, Internet Gateway, and VPC Endpoints organize connectivity and reduce direct exposure of the EC2 instance.

The next section focuses on deploying the EC2 web server and configuring Security Groups to control network access.

