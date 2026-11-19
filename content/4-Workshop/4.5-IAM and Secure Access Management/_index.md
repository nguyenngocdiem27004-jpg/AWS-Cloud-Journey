---
title: "IAM and Secure Access Management"
date: 2026-10-30
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

#### Overview

Identity and Access Management (IAM) is an important part of AWS infrastructure security. It allows administrators to define who can access AWS resources and which actions they are permitted to perform.

In this project, IAM roles and AWS Systems Manager Session Manager are used to provide secure administrative access to the private EC2 instance.

The main objective is to manage permissions without exposing the instance through a public IP address or opening an inbound SSH port.

### 1. IAM Role for EC2

The EC2 instance KLTN-Web-Server uses the IAM role KLTN-EC2-SSM-Role.

This role allows the instance to communicate with AWS Systems Manager and supports Session Manager functionality.

The role uses the AWS-managed policy:

- AmazonSSMManagedInstanceCore

This policy provides the permissions required for the EC2 instance to register with and communicate with Systems Manager.

![IAM role with AmazonSSMManagedInstanceCore policy](/images/4-Workshop/4.5-IAM%20and%20Secure%20Access%20Management/iam-role-policy.png)

### 2. Reviewing the IAM Role

To review the IAM role:

1. Open the AWS Management Console.
2. Navigate to **IAM**.
3. Select **Roles**.
4. Find KLTN-EC2-SSM-Role.
5. Review the attached permission policies.
6. Confirm that AmazonSSMManagedInstanceCore is attached.
7. Verify that the role is associated with the EC2 instance.

The IAM role allows the instance to obtain temporary permissions without storing long-term access keys on the server.

### 3. Secure Access Through Session Manager

AWS Systems Manager Session Manager provides browser-based and command-line access to managed EC2 instances.

Unlike traditional SSH access, Session Manager does not require an inbound SSH rule or a public IP address.

The project uses the following components:

- EC2 instance: KLTN-Web-Server

- IAM role: KLTN-EC2-SSM-Role

- Systems Manager permissions: AmazonSSMManagedInstanceCore

- VPC Endpoints: KLTN-SSM-Endpoint and KLTN-SSMMessages-Endpoint

The VPC Endpoints allow the private instance to communicate with Systems Manager through private network connectivity.

### 4. Establishing a Session Manager Connection

To access the EC2 instance:

1. Open the **EC2** console.
2. Select KLTN-Web-Server.
3. Click **Connect**.
4. Open the **Session Manager** tab.
5. Click **Connect** to start a session.

After the connection is established, a terminal session is available for administration.

The session can be used to check system services, review network settings, and manage the Nginx web server.

![Successful Systems Manager Session Manager terminal session](/images/4-Workshop/4.5-IAM%20and%20Secure%20Access%20Management/ssm-session.png)

### 5. Security Benefits

The IAM and Session Manager configuration provides several security benefits:

- **No inbound SSH requirement:** The instance does not need an open SSH port for administrative access.

- **No public IP requirement:** The private EC2 instance can be managed without direct Internet exposure.

- **Temporary permissions:** IAM roles provide temporary credentials instead of requiring long-term access keys on the instance.

- **Centralized access management:** IAM and Systems Manager help manage and control administrative access.

- **Private service connectivity:** VPC Endpoints allow communication with supported Systems Manager services through the VPC.

#### Verification Results

The implementation verified that:

- The IAM role KLTN-EC2-SSM-Role is assigned to the EC2 instance.

- The AmazonSSMManagedInstanceCore policy is attached.

- The SSM Agent is active on the instance.

- Session Manager can establish a connection to the private EC2 instance.

- The instance can be administered without a public IPv4 address or inbound SSH access.

### 6. Conclusion

This section demonstrates how IAM roles and AWS Systems Manager Session Manager can be used to manage a private EC2 instance securely.

By combining IAM permissions, Session Manager, and VPC Endpoints, the project reduces the need for direct network access and avoids exposing administrative services to the public Internet.

