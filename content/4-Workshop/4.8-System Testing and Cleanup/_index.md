---
title: "Security Testing and Infrastructure Review"
date: 2026-10-30
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

#### Overview

In this final section, we review and verify the AWS infrastructure deployed in this project.

The testing process focuses on the connectivity between AWS resources, EC2 web server availability, database network access, AWS WAF traffic filtering, and the monitoring and logging services.

The main objectives are to verify that the deployed resources operate as expected, review the security configurations, and identify resources that may generate unnecessary costs.

#### 1. Review the AWS Infrastructure

Before performing the tests, review the overall AWS architecture and confirm that the main resources are available.

The infrastructure includes:

- **Amazon VPC:** `KLTN-VPC`, using CIDR `10.0.0.0/16`.
- **Subnets:** Two public subnets and two private subnets.
- **Internet Gateway and NAT Gateway:** Provide internet connectivity according to the network design.
- **Amazon EC2:** `KLTN-Web-Server`, hosting the Nginx web server.
- **Amazon RDS:** `kltn-db`, providing the MySQL database service.
- **Application Load Balancer:** `KLTN-ALB`, receiving incoming web traffic.
- **AWS WAF:** `KLTN-WebACL`, associated with the Application Load Balancer.
- **Monitoring and logging:** Amazon CloudWatch, AWS CloudTrail, and AWS Config.

#### 2. Verify the EC2 Web Server

First, check the status of the EC2 instance.

1. Open the AWS Management Console.
2. Navigate to **EC2**.
3. Select **Instances**.
4. Locate `KLTN-Web-Server`.
5. Verify that the instance is in the **Running** state.
6. Check that the instance status checks have passed.

To verify the Nginx service, connect to the instance using AWS Systems Manager Session Manager and run:

```bash
sudo systemctl status nginx
```

The service should be active and running.

The web server can also be accessed through the DNS name of the Application Load Balancer to verify that incoming HTTP requests are forwarded successfully.

#### 3. Verify the Application Load Balancer

The Application Load Balancer distributes incoming web traffic to registered targets.

To verify its operation:

1. Open the EC2 console.
2. Select **Load Balancers**.
3. Open `KLTN-ALB`.
4. Review its status and DNS name.
5. Open the **Target Groups** section.
6. Check the health status of the registered EC2 target.

During implementation, the target group showed one healthy target and no unhealthy targets.

Accessing the ALB DNS name also displayed the default Nginx welcome page, confirming that the web server was reachable through the load balancer.

#### 4. Verify Connectivity Between EC2 and RDS

The next test checks network connectivity between the EC2 instance and the RDS MySQL database.

The RDS Security Group is configured to allow MySQL traffic on TCP port `3306` from the EC2 Security Group.

The connection can be tested from the EC2 instance using:

```bash
nc -zv <RDS-endpoint> 3306
```

During the implementation, the connection test returned:

```text
Connected to 10.0.2.198:3306
```

This confirms that the EC2 instance can establish a TCP connection to the RDS database through port 3306.

**Note:** This test verifies network connectivity only. Application-level database queries and data processing have not been demonstrated.

#### 5. Review AWS WAF Traffic Filtering

AWS WAF is associated with `KLTN-ALB` to inspect incoming web requests.

To review the configuration and traffic statistics:

1. Open **AWS WAF & Shield**.
2. Select **Web ACLs**.
3. Open `KLTN-WebACL`.
4. Verify that `KLTN-ALB` is associated with the Web ACL.
5. Review the request statistics.

During the implementation, the Web ACL dashboard displayed:

| Request action | Number of requests |
|---|---:|
| Allowed | 5 |
| Blocked | 25 |
| Total | 30 |

These results demonstrate that AWS WAF processed incoming requests and applied its configured filtering rules.

#### 6. Review Monitoring and Logging Services

The monitoring and logging services provide information about resource performance, account activities, and infrastructure configurations.

**Amazon CloudWatch**

Review the available EC2 metrics, such as:

- `CPUUtilization`
- `NetworkIn`
- `NetworkOut`

These metrics help observe the operational status and resource utilization of the EC2 instance.

**AWS CloudTrail**

Review the CloudTrail configuration and available event history to identify recorded account activities and management events.

**AWS Config**

Review the resource inventory and recording status.

During the implementation, AWS Config recording was enabled, and the resource inventory displayed 24 resources.

The compliance status of individual rules should be reviewed separately. Do not assume that all resources are compliant without checking their evaluation results.

#### 7. Review AWS Resource Usage and Costs

Before completing the project, review AWS resources that may generate charges.

Open the AWS Management Console and check the following services:

- **EC2:** Review running instances and attached storage volumes.
- **Elastic IP addresses:** Check allocated addresses and their associations.
- **EBS Volumes:** Review volumes that are no longer required.
- **Snapshots:** Review retained snapshots.
- **NAT Gateway:** Check its status and associated costs.
- **Application Load Balancer:** Review whether it is still required.
- **Amazon RDS:** Check the database instance and storage configuration.
- **AWS WAF:** Review the Web ACL and associated usage.
- **CloudWatch:** Review any additional monitoring resources.

Estimated spending can also be reviewed through **Billing and Cost Management**.

**Important:** Stopping an EC2 instance does not stop every related charge. NAT Gateways, load balancers, RDS instances, storage volumes, and other retained resources may continue to incur costs.

#### 8. Save Evidence and Review Cleanup Requirements

Before stopping or deleting any AWS resource, save the screenshots and test results required for the project report and demonstration.

Recommended evidence includes:

1. VPC and subnet configuration.
2. EC2 instance status and instance checks.
3. EC2 Security Group inbound rules.
4. RDS Security Group inbound rule for TCP 3306.
5. Successful EC2-to-RDS connectivity test.
6. Application Load Balancer and healthy target status.
7. Nginx welcome page accessed through the ALB DNS name.
8. AWS WAF association and request statistics.
9. CloudWatch EC2 metrics.
10. CloudTrail event history.
11. AWS Config recording status and resource inventory.

After saving the evidence, identify resources that are no longer required.

Only stop or delete resources after reviewing their dependencies and confirming that they are not needed for the project demonstration or report.

Do not delete shared network components or resources that are still required by other services.

#### 9. Final Infrastructure Evaluation

Based on the implementation and verification activities, the main results can be summarized as follows:

| Component | Verification result |
|---|---|
| VPC and network infrastructure | Deployed |
| EC2 instance | Running; status checks passed |
| Nginx web server | Accessible through ALB |
| Application Load Balancer | Active; one healthy target |
| EC2-to-RDS connectivity | TCP port 3306 connection successful |
| AWS WAF | Associated with ALB; 30 requests recorded |
| CloudTrail | Created |
| AWS Config | Recording enabled; 24 resources listed |
| CloudWatch | Used to review resource metrics |

These results demonstrate the operation of the main AWS infrastructure components and the security controls implemented in the project.

#### Conclusion

In this final section, we reviewed and verified the AWS infrastructure deployed in the project.

The tests confirmed that the EC2 web server was accessible through the Application Load Balancer, the EC2 instance could establish a TCP connection to the RDS MySQL database, and AWS WAF processed incoming web requests.

We also reviewed CloudWatch, CloudTrail, and AWS Config to understand how AWS provides monitoring, activity recording, and resource configuration tracking.

The project results provide a practical demonstration of AWS network infrastructure deployment and the application of security controls to protect cloud resources.