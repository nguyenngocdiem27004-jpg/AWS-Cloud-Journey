---
title: "Project Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Research and Implementation of Infrastructure Security on AWS

## 1. Executive Summary

The **Research and Implementation of Infrastructure Security on AWS** project aims to study and implement security mechanisms for cloud infrastructure using Amazon Web Services (AWS).

The project focuses on designing and deploying a secure AWS network environment using Amazon Virtual Private Cloud (VPC), public and private subnets, Internet Gateway, and NAT Gateway. Compute and database resources are deployed using Amazon EC2 and Amazon RDS, while an Application Load Balancer (ALB) provides an entry point for web traffic.

To improve infrastructure security, the project applies Identity and Access Management (IAM), Security Groups, AWS Web Application Firewall (AWS WAF), and network access control configurations. Monitoring and auditing are supported by Amazon CloudWatch, AWS CloudTrail, and AWS Config.

The implementation is conducted in a practical AWS lab environment. The project evaluates network connectivity, access permissions, web request filtering, resource monitoring, and configuration compliance. The final result is an AWS infrastructure model with multiple security layers and documented test evidence.

## 2. Problem Statement

### Current Challenges

Cloud infrastructure provides flexible computing, storage, and networking resources. However, deploying cloud resources without appropriate security configurations may expose systems to unauthorized access, unnecessary network traffic, and configuration risks.

Common challenges include:

- Publicly exposing resources that should only be accessible through private networks.
- Configuring overly permissive inbound and outbound network rules.
- Assigning unnecessary permissions to users, groups, or service roles.
- Lacking sufficient visibility into resource activities and system performance.
- Having difficulty identifying configuration issues and evaluating security compliance.
- Incurring unexpected costs when cloud resources remain active without being used.

These challenges demonstrate the need for a structured approach to designing, implementing, monitoring, and evaluating cloud infrastructure security.

### Proposed Solution

The project develops a multi-layer security architecture on AWS. The proposed solution includes the following components:

- **Network Infrastructure:** Amazon VPC provides an isolated network environment with public and private subnets. Internet Gateway and NAT Gateway support controlled network connectivity.
- **Compute Resources:** Amazon EC2 hosts the web server and provides a practical environment for testing infrastructure access and security configurations.
- **Database Resources:** Amazon RDS provides a managed database service deployed in private subnets. Access is restricted to authorized resources.
- **Load Balancing:** Application Load Balancer distributes incoming HTTP requests to the EC2 target and provides a controlled application entry point.
- **Access Control:** IAM manages identities and permissions, while Security Groups restrict traffic between the ALB, EC2, and RDS resources.
- **Web Protection:** AWS WAF filters incoming web requests based on configured Web ACL rules.
- **Monitoring and Auditing:** CloudWatch monitors available resource metrics, CloudTrail records account activities and API events, and AWS Config evaluates resource configurations against selected rules.
- **Security Testing:** Connectivity tests, access control checks, and web request filtering tests are performed to evaluate the deployed security mechanisms.

The project is implemented in a lab environment to demonstrate how AWS services can work together to protect cloud infrastructure.

### Benefits and Return on Investment (ROI)

The project is expected to provide the following benefits:

- Improve network isolation by separating public-facing and private resources.
- Restrict access to cloud resources through IAM permissions and Security Group rules.
- Add a web application protection layer through AWS WAF.
- Improve visibility into resource performance and account activities through monitoring and audit services.
- Support configuration assessment and identification of potential security issues.
- Provide practical experience in cloud networking, infrastructure deployment, and security management.
- Establish a reusable foundation that can be extended with additional security services.

As this is an academic research and lab implementation project, its value will be evaluated through technical results, security tests, resource management, and operating costs rather than an assumed financial payback period.

## 3. Solution Architecture

The system adopts a multi-layer AWS infrastructure security architecture. Amazon VPC provides the main network environment, which is divided into public and private subnets according to resource functions and access requirements.

The public subnets contain the Application Load Balancer and networking components that require public connectivity. Private subnets are used for backend resources such as the EC2 instance and RDS database, according to the implemented network design.

The main traffic flow is as follows:

1. Users send HTTP requests to the DNS endpoint of the Application Load Balancer.
2. The ALB forwards permitted requests to the registered EC2 target.
3. AWS WAF inspects incoming web requests associated with the ALB and applies the configured Web ACL rules.
4. The EC2 instance hosts the web server and communicates with the RDS database through the permitted database port.
5. Security Groups restrict traffic between the ALB, EC2, and RDS resources.
6. IAM roles and policies control access to AWS services and resources.
7. CloudWatch provides monitoring information, CloudTrail records account activities, and AWS Config evaluates resource configurations.

### AWS Services and Technologies

- **Amazon VPC:** Provides an isolated virtual network environment for AWS resources.
- **Public and Private Subnets:** Separate resources according to their network exposure and access requirements.
- **Internet Gateway:** Enables internet connectivity for resources routed through public subnets.
- **NAT Gateway:** Allows resources in private subnets to initiate outbound internet connections without requiring direct inbound internet access.
- **Amazon EC2:** Provides virtual servers for hosting the web server and performing infrastructure security tests.
- **Amazon RDS:** Provides a managed relational database service within the private network environment.
- **Application Load Balancer:** Distributes incoming application traffic to registered targets.
- **AWS IAM:** Manages users, roles, policies, and permissions based on the principle of least privilege.
- **Security Groups:** Act as virtual firewalls controlling inbound and outbound traffic for supported resources.
- **AWS WAF:** Inspects web requests and applies filtering rules through Web ACLs.
- **Amazon CloudWatch:** Provides monitoring metrics and log management capabilities for supported AWS resources.
- **AWS CloudTrail:** Records account activities and API events for auditing.
- **AWS Config:** Records resource configurations and evaluates them against selected compliance rules.

### Component Design

**Network Infrastructure**

Amazon VPC is configured with a CIDR address range and divided into public and private subnets. Route tables define traffic paths between subnets, the Internet Gateway, and the NAT Gateway. This structure supports network separation and controlled connectivity.

**Compute and Database Layer**

Amazon EC2 hosts the web server in the AWS network environment. Amazon RDS provides database services in private subnets. Communication between EC2 and RDS is restricted through Security Group rules and the required database port.

**Application Access Layer**

Application Load Balancer provides an entry point for web traffic and forwards requests to healthy registered targets. AWS WAF is associated with the ALB to inspect and filter incoming requests based on configured rules.

**Identity and Access Management Layer**

IAM users, roles, and policies define which identities and AWS services can access specific resources. Permissions are designed according to the principle of least privilege.

**Monitoring and Auditing Layer**

CloudWatch provides visibility into available resource metrics and monitoring information. CloudTrail records account activities and API calls. AWS Config records resource configurations and evaluates selected security rules.

**Security Layer**

The security architecture combines network isolation, Security Groups, IAM permissions, and AWS WAF. These controls work together to reduce unnecessary exposure and restrict access to authorized traffic and identities.

## 4. Technical Implementation

### Implementation Phases

The project is divided into four main phases.

**Phase 1: Research and Architecture Design**

- Study AWS cloud infrastructure and the shared responsibility model.
- Research VPC, subnetting, routing, and AWS network security mechanisms.
- Identify security requirements for compute, database, and application access.
- Design the network architecture, CIDR address plan, and resource placement.
- Identify suitable AWS services for access control, monitoring, and auditing.

**Phase 2: AWS Network and Resource Deployment**

- Create an Amazon VPC with an appropriate CIDR address range.
- Create public and private subnets across availability zones.
- Configure the Internet Gateway, NAT Gateway, and route tables.
- Deploy an EC2 instance and configure secure administrative access.
- Create an RDS database and configure its subnet group.
- Configure Security Groups to control communication between resources.
- Deploy an Application Load Balancer and verify target health.

**Phase 3: Security Configuration and Monitoring**

- Configure IAM roles and policies for appropriate resource access.
- Review Security Group rules and restrict unnecessary traffic.
- Create and associate an AWS WAF Web ACL with the Application Load Balancer.
- Configure and review CloudTrail activity records.
- Use CloudWatch to inspect available resource metrics and monitoring information.
- Review AWS Config recording status and selected compliance rules.

**Phase 4: Testing, Evaluation, and Documentation**

- Test network connectivity between the EC2 instance and RDS database.
- Verify web server access through the ALB DNS endpoint.
- Test permitted and restricted traffic based on Security Group rules.
- Perform controlled web request tests to evaluate AWS WAF behavior.
- Review CloudWatch metrics, CloudTrail records, and AWS Config results.
- Evaluate resource usage and identify cost optimization opportunities.
- Complete architecture diagrams, configuration descriptions, screenshots, and test reports.

### Technical Requirements

**Network Infrastructure**

- Use Amazon VPC to create an isolated network environment.
- Divide the network into public and private subnets.
- Configure route tables, Internet Gateway, and NAT Gateway according to the network design.
- Apply appropriate routing and subnet associations.
- Restrict unnecessary traffic between network components.

**Compute and Database Infrastructure**

- Deploy an EC2 instance using a suitable Amazon Machine Image.
- Configure secure administrative access, preferably using AWS Systems Manager Session Manager where applicable.
- Deploy an RDS database in private subnets.
- Configure the database Security Group to allow connections only from authorized resources.
- Verify connectivity through the required database port without assuming that application-level data queries have been completed.

**Application and Web Protection**

- Deploy a web server on EC2.
- Configure an Application Load Balancer and target group.
- Verify target health and application access through the ALB DNS endpoint.
- Associate AWS WAF with the ALB and configure appropriate Web ACL rules.
- Test normal and controlled suspicious requests to evaluate filtering behavior.

**Monitoring and Auditing**

- Use CloudWatch to inspect supported resource metrics and monitoring information.
- Use CloudTrail to review account activities and API events.
- Use AWS Config to record resource configurations and evaluate selected rules.
- Review available logs and monitoring results to support security analysis.

**Security Management**

- Apply IAM permissions according to the principle of least privilege.
- Configure Security Groups to allow only required traffic.
- Keep database resources in private subnets.
- Avoid exposing administrative and monitoring interfaces unnecessarily.
- Review security configurations regularly and document test results.

## 5. Implementation Timeline and Milestones

The project follows a series of milestones during the internship and implementation period from August to December 2026.

- **Phase 1 – Research and Design:** Study AWS services, infrastructure security principles, network architecture, and IP addressing.
- **Phase 2 – Network Deployment:** Create the VPC, public and private subnets, Internet Gateway, NAT Gateway, and route tables.
- **Phase 3 – Compute and Database Deployment:** Deploy EC2 and RDS, configure Security Groups, and verify database connectivity.
- **Phase 4 – Application Access Deployment:** Configure the web server, Application Load Balancer, target group, and application access.
- **Phase 5 – Security and Monitoring:** Configure IAM, AWS WAF, CloudTrail, CloudWatch, and AWS Config.
- **Phase 6 – Testing and Finalization:** Perform connectivity and security tests, review monitoring results, evaluate costs, and complete the project documentation.

The project can be extended in the future through additional security services, automated configuration management, more advanced monitoring, and improved security testing.

## 6. Estimated Budget

The project's cost depends on the AWS resources used, their configurations, operating duration, storage capacity, data transfer, and selected service features.

The [AWS Pricing Calculator](https://calculator.aws/) can be used to estimate costs based on the planned infrastructure.

### Cost Components

- **Amazon EC2:** Costs depend on instance type, operating system, and running time.
- **Amazon EBS:** Storage costs depend on volume type, provisioned capacity, and applicable usage.
- **Amazon RDS:** Costs depend on database instance type, storage, backup configuration, and running time.
- **NAT Gateway:** Charges may include hourly usage and data processing.
- **Application Load Balancer:** Charges depend on operating time and applicable capacity units.
- **AWS WAF:** Costs may depend on the number of Web ACLs, rules, and web requests.
- **Amazon CloudWatch:** Charges may apply to metrics, logs, alarms, and other features beyond applicable free allowances.
- **AWS CloudTrail and AWS Config:** Costs depend on the selected event, recording, delivery, and evaluation features.
- **Data Transfer:** Charges may apply depending on the type and amount of data transferred.

### Cost Optimization Strategies

- Stop EC2 instances when they are not needed for testing or demonstrations.
- Review RDS usage and stop or remove resources when appropriate and permitted.
- Release unused Elastic IP addresses and remove unnecessary networking resources after checking dependencies.
- Review NAT Gateway and ALB usage because these resources may incur charges while active.
- Select resource configurations that match the actual workload.
- Monitor AWS Billing and configure budget alerts.
- Collect required screenshots, logs, and project evidence before stopping or deleting resources.
- Check for dependencies before releasing resources to avoid disrupting other components.

The final cost evaluation should use actual billing information and the AWS Pricing Calculator. Costs should not be assumed to be zero simply because a resource is covered by a free usage allowance or promotional credits.

## 7. Risk Assessment

### Risk Matrix

- **Unauthorized Access:** High impact if IAM permissions or network access rules are configured too broadly.
- **Network Misconfiguration:** High impact if subnet associations, route tables, or gateway routes are incorrect.
- **Database Exposure:** High impact if the RDS database is accessible from unauthorized networks.
- **Web Application Attacks:** Medium to high impact if incoming requests are not appropriately inspected and filtered.
- **Insufficient Monitoring:** Medium impact if resource activities or security events are not adequately recorded.
- **Unexpected AWS Costs:** Medium to high impact if billable resources remain active longer than necessary.
- **Configuration Non-Compliance:** Medium impact if AWS resources do not meet selected security rules.

### Risk Mitigation Strategies

- **Access Control:** Apply least-privilege IAM policies and review permissions regularly.
- **Network Security:** Separate public and private resources, restrict Security Group rules, and verify route table configurations.
- **Database Security:** Keep RDS in private subnets and allow database connections only from authorized resources.
- **Web Protection:** Associate AWS WAF with the ALB and test configured filtering rules.
- **Monitoring and Auditing:** Review CloudWatch metrics, CloudTrail records, and AWS Config compliance results.
- **Cost Management:** Monitor billing, configure budget alerts, and stop or release unnecessary resources after collecting required evidence.
- **Configuration Management:** Document infrastructure settings and review changes to reduce configuration errors.

### Contingency Plan

If the web application becomes unavailable, check the EC2 instance status, web server service, ALB listener, target group health, and Security Group rules.

If EC2 cannot connect to RDS, verify the database status, subnet routing, Security Group source rules, database port, and connection configuration.

If unexpected access is allowed or legitimate requests are blocked, review the AWS WAF Web ACL rules, rule priority, and request metrics. Adjust configurations only after identifying the cause.

If monitoring information is unavailable, review service configuration, resource permissions, recording status, and the availability of the relevant metrics or logs.

Before stopping or deleting any resource during cleanup, preserve the screenshots and test evidence required for the project report and demonstration.

## 8. Expected Outcomes

### Technical Improvements

- Build an AWS infrastructure environment with public and private network segments.
- Deploy EC2 and RDS resources with controlled network access.
- Configure an Application Load Balancer to provide web application access.
- Apply IAM roles and policies based on the principle of least privilege.
- Use Security Groups to control traffic between infrastructure components.
- Integrate AWS WAF with the ALB to inspect and filter web requests.
- Use CloudWatch, CloudTrail, and AWS Config to support monitoring, auditing, and configuration assessment.
- Perform connectivity and security tests and document the results.

### Long-Term Value

The project provides a practical foundation for understanding AWS infrastructure security, cloud networking, access control, and monitoring.

The architecture can be extended with additional security services, automated deployment, centralized log analysis, advanced alerting, and more comprehensive security testing.

Through this project, the implementer can apply computer networking knowledge to AWS cloud environments and gain practical experience in infrastructure deployment, resource management, security configuration, and technical documentation.

The final results will be evaluated based on network connectivity, service availability, access control effectiveness, web request filtering behavior, monitoring information, configuration assessment, and resource costs.