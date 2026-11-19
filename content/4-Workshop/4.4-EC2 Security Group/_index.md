---
title: "Deployment of Amazon EC2 and Security Group Configuration"
date: 2026-10-30
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

### 1. Overview of Amazon EC2

Amazon Elastic Compute Cloud (Amazon EC2) provides virtual servers in the AWS Cloud. It allows users to deploy and manage computing resources without maintaining physical servers.

In this project, an EC2 instance named KLTN-Web-Server hosts the Nginx web server. The instance is deployed in a private subnet and receives web traffic through the Application Load Balancer (ALB).

The instance does not have a public IPv4 address. Administrative access is provided through AWS Systems Manager Session Manager.

#### Deployment Objectives

- Deploy an EC2 instance inside the project VPC.

- Place the instance in a private subnet.

- Attach an IAM role for Systems Manager access.

- Use Session Manager for secure administration.

- Install and verify the Nginx web server.

- Configure Security Groups to restrict network traffic.

### 2. EC2 Instance Configuration

| Component | Configuration |
|---|---|
| Instance Name | KLTN-Web-Server |
| Instance Type | t3.micro |
| VPC | KLTN-VPC |
| Subnet | KLTN-Private-Subnet |
| Private IPv4 | 10.0.2.35 |
| Public IPv4 | Not assigned |
| Web Server | Nginx |
| Management Method | AWS Systems Manager Session Manager |
| IAM Role | KLTN-EC2-SSM-Role |

![KLTN-Web-Server EC2 instance configuration](/images/4-Workshop/4.4-EC2%20Security%20Group/ec2-instance.png)

#### Reviewing the EC2 Instance

To review the deployed instance:

1. Open the **Amazon EC2** service.
2. Select **Instances**.
3. Find KLTN-Web-Server.
4. Review its instance type, VPC, subnet, private IP address, and public IP address.
5. Confirm that the instance is running and its status checks have passed.

The instance is deployed in the private network to reduce direct exposure to the Internet.

![EC2 network details showing its private IP and no public IPv4 address](/images/4-Workshop/4.4-EC2%20Security%20Group/ec2-network.png)

### 3. Configuring IAM Role for Systems Manager

AWS Systems Manager Session Manager allows administrators to access an EC2 instance without opening an inbound SSH port or managing SSH key pairs.

The project uses the IAM role KLTN-EC2-SSM-Role with the AWS-managed policy AmazonSSMManagedInstanceCore.

To review the role:

1. Open the **IAM** service.
2. Select **Roles**.
3. Find KLTN-EC2-SSM-Role.
4. Review its trusted entity and attached permissions.
5. Confirm that the role is assigned to KLTN-Web-Server.

The EC2 instance uses this role to communicate with Systems Manager.

### 4. Accessing the Instance Through Session Manager

To establish a management session:

1. Open the **EC2** console.
2. Select KLTN-Web-Server.
3. Click **Connect**.
4. Select **Session Manager**.
5. Start the session.

The session provides terminal access without requiring a public IP address or inbound SSH access.

### 5. Configuring Security Groups

A Security Group acts as a virtual firewall for AWS resources. It controls inbound and outbound traffic according to defined rules.

The project applies Security Groups to restrict access to the web server and supporting network components.

| Component | Protocol | Port | Purpose |
|---|---|---|---|
| ALB Security Group | TCP | 80 | Receive HTTP requests |
| EC2 Security Group | TCP | 80 | Allow HTTP traffic forwarded by the ALB |
| VPC Endpoint Security Group | TCP | 443 | Allow HTTPS communication from the EC2 instance |

The EC2 Security Group is configured to allow web traffic from the ALB Security Group rather than directly from arbitrary Internet sources.

No inbound SSH rule is required for administration because Session Manager is used.

![EC2 Security Group rules](/images/4-Workshop/4.4-EC2%20Security%20Group/security-group.png)

### 6. Installing and Verifying Nginx

Nginx is the web server installed on the EC2 instance.

After connecting through Session Manager, the following commands can be used on Ubuntu:

```bash
sudo apt update
sudo apt install nginx -y
```

Start and enable the service:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Check the service:

```bash
sudo systemctl status nginx
```

To verify the local web server response:

```bash
curl -I http://localhost
```

A successful HTTP response confirms that Nginx is responding locally on the instance.

### 7. Verification Results

The following configurations were verified during implementation:

- KLTN-Web-Server is running.

- The instance uses private IP address 10.0.2.35.

- No public IPv4 address is assigned.

- The instance has the KLTN-EC2-SSM-Role IAM role.

- Session Manager can establish a terminal session.

- Nginx is running and responds to local HTTP requests.

#### Expected Results

The project has a private EC2 web server running Nginx. Session Manager provides administrative access, while Security Groups restrict network communication to the required traffic.

This configuration reduces direct exposure of the server and provides a foundation for web traffic protection through the Application Load Balancer and AWS WAF.

