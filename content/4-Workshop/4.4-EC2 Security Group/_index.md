---
title: "Deployment of Amazon EC2 and Security Group Configuration"
date: 2026-10-30
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

#### Overview of Amazon EC2

Amazon Elastic Compute Cloud (Amazon EC2) is an AWS service that provides virtual servers in the cloud. It allows users to run applications and services without maintaining physical servers.

In this project, an EC2 instance named `KLTN-Web-Server` is deployed to host the Nginx web server. The instance is part of the private network architecture and receives web traffic through the Application Load Balancer (ALB).

The instance is also configured with an IAM role to support secure management through AWS Systems Manager Session Manager.

#### Deployment Objectives

- Deploy an EC2 instance for the project's web server.
- Place the instance in the appropriate subnet of `KLTN-VPC`.
- Configure an IAM role to support Systems Manager access.
- Use Session Manager to access and manage the instance without requiring direct SSH access.
- Install and verify the Nginx web server.
- Configure Security Groups to control traffic between the ALB, EC2 instance, and RDS database.

#### EC2 Instance Specifications

| Component | Configuration |
|---|---|
| Instance Name | `KLTN-Web-Server` |
| Operating System | Ubuntu Server |
| VPC | `KLTN-VPC` |
| Subnet | Private subnet |
| Web Server | Nginx |
| Management Method | AWS Systems Manager Session Manager |
| IAM Role | EC2 IAM role for Systems Manager access |

#### Deploying an EC2 Instance

Follow these steps:

1. Access the **AWS Management Console**.
2. Open the **Amazon EC2** service.
3. Select **Instances**, then click **Launch instances**.
4. Enter `KLTN-Web-Server` as the instance name.
5. Select an appropriate Ubuntu Server Amazon Machine Image (AMI).
6. Choose an instance type according to the project requirements and available budget.
7. Under **Network settings**, select the VPC `KLTN-VPC`.
8. Select the appropriate private subnet.
9. Configure the Security Group for the required network connections.
10. Attach the IAM role that allows the instance to be managed through AWS Systems Manager.
11. Configure the storage capacity according to the project requirements.
12. Review the configuration and click **Launch instance**.

After launching the instance, verify that its state is **Running** and that its status checks have passed.

#### Configuring IAM Role for Systems Manager

AWS Systems Manager Session Manager provides a way to access an EC2 instance without opening an inbound SSH port or managing SSH key pairs.

To use Session Manager, the EC2 instance must have an IAM role with the required Systems Manager permissions.

The configuration process includes:

1. Open the **IAM** service in the AWS Management Console.
2. Create or select an IAM role for EC2.
3. Attach the required Systems Manager permissions, such as the `AmazonSSMManagedInstanceCore` policy.
4. Return to the EC2 console.
5. Select the instance `KLTN-Web-Server`.
6. Attach the IAM role to the instance if it has not already been assigned.
7. Verify that the instance can connect to Systems Manager.

After the configuration is complete, select the EC2 instance and use **Connect** → **Session Manager** to open a terminal session.

#### Configuring Security Groups

A Security Group acts as a virtual firewall that controls inbound and outbound traffic for AWS resources. It helps restrict network access to only the connections required by the system.

In this project, Security Groups are configured to control communication between the Application Load Balancer, EC2 web server, and RDS database.

The main access rules follow this structure:

| Resource | Protocol | Port | Source / Destination | Purpose |
|---|---|---|---|---|
| ALB Security Group | TCP | 80 | Client access, according to the ALB configuration | Receive web requests |
| EC2 Security Group | TCP | 80 | ALB Security Group | Allow the ALB to forward HTTP traffic to Nginx |
| RDS Security Group | TCP | 3306 | EC2 Security Group | Allow the EC2 instance to connect to MySQL |

The EC2 Security Group does not need a public SSH inbound rule when Session Manager is used for administration. Monitoring ports such as `3000`, `9090`, and `9100` are not included because Grafana, Prometheus, and Node Exporter are not part of this deployment.

**Security considerations:**

- Allow HTTP traffic to the EC2 instance only from the ALB Security Group.
- Allow MySQL traffic to RDS only from the EC2 Security Group.
- Avoid exposing administrative ports directly to the Internet.
- Apply the principle of least privilege when defining inbound and outbound rules.
- Security Groups are stateful, so response traffic for permitted connections is automatically allowed.

#### Installing and Verifying Nginx

Nginx is used as the web server running on the EC2 instance.

After connecting to the instance through Session Manager, the administrator can install Nginx on Ubuntu using the following commands:

```bash
sudo apt update
sudo apt install nginx -y
```

Start the Nginx service and configure it to start automatically:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Check the service status:

```bash
sudo systemctl status nginx
```

If Nginx is running correctly, the web server can respond to HTTP requests forwarded by the Application Load Balancer.

#### Verifying EC2 and Security Group Configuration

After completing the configuration, verify the following:

- The EC2 instance `KLTN-Web-Server` is in the **Running** state.
- The instance status checks have passed.
- The instance has the required IAM role for Systems Manager.
- Session Manager can establish a session with the instance.
- The Nginx service is running.
- The EC2 Security Group allows HTTP traffic from the ALB Security Group.
- The RDS Security Group allows MySQL traffic on port `3306` from the EC2 Security Group.

Network connectivity between EC2 and RDS can also be checked separately to verify that the required database port is reachable.

#### Expected Results

After completing this section, the project has an EC2 instance running Nginx as its web server. Administrative access is provided through AWS Systems Manager Session Manager, while Security Groups restrict communication between the ALB, EC2 instance, and RDS database.

These configurations provide a foundation for deploying and protecting the web service within the AWS infrastructure.