---
title: "Worklog Week 10"
date: 2026-10-17
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

- Perform overall testing of the AWS infrastructure security system.
- Verify network connectivity between AWS resources deployed in public and private subnets.
- Evaluate the operation of EC2, RDS, and the Application Load Balancer.
- Test security configurations, including Security Groups, AWS WAF, and IAM permissions.
- Review monitoring, logging, and resource compliance information through CloudWatch, CloudTrail, and AWS Config.
- Evaluate AWS service costs and propose measures to optimize resource usage.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Review the overall architecture of the AWS infrastructure security system.<br>- Check the status of the VPC, public and private subnets, Internet Gateway, NAT Gateway, and Route Tables.<br>- Review the EC2, RDS, and ALB configurations.<br>- Identify the main components and security functions that need to be tested. | 17/10/2026 | 17/10/2026 | [AWS Documentation](https://docs.aws.amazon.com/) |
| 3 | - Verify network connectivity between the EC2 instance and the RDS database.<br>- Check the database connection through the configured security rules and port 3306.<br>- Test access to the web server through the ALB DNS name.<br>- Record the test results and any issues encountered. | 18/10/2026 | 19/10/2026 | [Amazon EC2 Documentation](https://docs.aws.amazon.com/ec2/)<br>[Amazon RDS Documentation](https://docs.aws.amazon.com/rds/) |
| 4 | - Review Security Group rules between the ALB, EC2, and RDS resources.<br>- Perform basic access tests to evaluate the AWS WAF rules.<br>- Review CloudWatch monitoring metrics and CloudTrail activity records.<br>- Check AWS Config recording status and resource compliance results.<br>- Review IAM permissions and apply the principle of least privilege where appropriate. | 20/10/2026 | 21/10/2026 | [AWS WAF Documentation](https://docs.aws.amazon.com/waf/)<br>[AWS CloudTrail Documentation](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| 5 | - Review AWS service usage and estimated costs during deployment.<br>- Identify resources that may incur charges when they are not in use, such as EC2, EBS, NAT Gateway, and RDS.<br>- Propose cost optimization measures, including stopping or releasing unnecessary resources after collecting the required project evidence.<br>- Summarize the implementation and testing results, evaluate the strengths and limitations of the system, and propose improvements. | 22/10/2026 | 23/10/2026 | [AWS Pricing](https://aws.amazon.com/pricing/) |

### Week 10 Results:

- Reviewed and evaluated the overall architecture of the AWS infrastructure security system.
- Verified network connectivity between EC2 and RDS through the configured database port.
- Checked the operation of the web server through the Application Load Balancer.
- Reviewed Security Group rules and evaluated AWS WAF request filtering through basic tests.
- Examined CloudWatch metrics, CloudTrail activity records, and AWS Config compliance information.
- Reviewed IAM permissions and the importance of applying the principle of least privilege.
- Identified AWS resources that may generate costs and learned basic cost optimization measures.
- Summarized the implementation and testing results and identified possible improvements to the AWS infrastructure security system.