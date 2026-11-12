---
title: "Connectivity Between Amazon EC2 and Amazon RDS"
date: 2026-10-30
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

#### Overview

This section describes the network connectivity between the Amazon EC2 instance and the Amazon RDS MySQL database within the AWS environment.

The EC2 instance, `KLTN-Web-Server`, is used as the web server, while the RDS instance, `kltn-db`, provides the database service. Communication between these resources is controlled by their associated Security Groups.

The objective is to allow the EC2 instance to access the RDS database through the MySQL port (TCP 3306), while restricting database access to authorized resources.

#### 1. Prepare the Environment

Before testing the connection, verify that the following resources are available:

- An existing VPC named `KLTN-VPC`.
- An EC2 instance named `KLTN-Web-Server`.
- An RDS MySQL instance named `kltn-db`.
- Security Groups associated with the EC2 and RDS instances.
- Network routes that allow communication between the resources.

The EC2 instance and RDS database are deployed within the AWS VPC. The RDS instance uses a DB subnet group containing private subnets.

#### 2. Configure the Security Groups

Security Groups control network traffic to and from AWS resources. To allow the EC2 instance to connect to the RDS database, configure the inbound rules of the RDS Security Group.

**EC2 Security Group**

The EC2 Security Group allows HTTP traffic from the Application Load Balancer Security Group.

**RDS Security Group**

Configure the following inbound rule:

| Type | Protocol | Port | Source |
|---|---|---|---|
| MySQL/Aurora | TCP | 3306 | EC2 Security Group |

Using the EC2 Security Group as the source restricts database access to the authorized EC2 instance instead of allowing connections from all IP addresses.

#### 3. Verify the Database Connectivity

After configuring the Security Groups, use the EC2 instance to test connectivity to the RDS database.

The connection test checks whether the EC2 instance can reach the database endpoint through TCP port 3306.

Example command:

```bash
nc -zv <RDS-endpoint> 3306
```

Replace `<RDS-endpoint>` with the actual endpoint or reachable database address.

A successful connection indicates that the network path and Security Group rules allow traffic through the MySQL port.

#### 4. Test Results

During the implementation, the connection from the EC2 instance to the RDS MySQL database was tested successfully.

The test returned the following connection message:

```text
Connected to 10.0.2.198:3306
```

This confirms that the EC2 instance can establish a TCP connection to the RDS database on port 3306.

**Note:** This test verifies network connectivity only. Reading, querying, or processing application data from the database has not been demonstrated in this step.

#### Conclusion

In this section, the network access between Amazon EC2 and Amazon RDS was configured and tested using Security Groups.

The successful TCP connection on port 3306 confirms that the EC2 instance can reach the MySQL database through the configured network path. Restricting the RDS inbound rule to the EC2 Security Group also helps reduce unauthorized database access.