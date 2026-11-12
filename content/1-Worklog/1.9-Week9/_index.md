---
title: "Worklog Week 9"
date: 2026-10-10
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

- Learn about AWS Web Application Firewall (AWS WAF) and its role in protecting web applications.
- Review the Web ACL configuration and its association with the Application Load Balancer (ALB).
- Understand how AWS WAF rules inspect incoming web requests.
- Perform basic tests to evaluate the ability of AWS WAF to allow or block requests.
- Review monitoring information and prepare security testing evidence.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Learn about the architecture and operating principles of AWS WAF.<br>- Understand the role of Web ACLs and rules in filtering incoming web requests.<br>- Review the ALB deployed in previous weeks.<br>- Check the association between the Web ACL and the ALB. | 10/10/2026 | 10/10/2026 | [AWS WAF Documentation](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |
| 3 | - Access the AWS WAF console and review the Web ACL configuration.<br>- Examine the configured rules and their actions.<br>- Review the default action and rule priority.<br>- Check the integration status between AWS WAF and the ALB. | 11/10/2026 | 12/10/2026 | [AWS WAF Documentation](https://docs.aws.amazon.com/waf/latest/developerguide/web-acl.html) |
| 4 | - Perform basic access tests through the ALB DNS name.<br>- Send normal requests and review whether they are allowed.<br>- Perform controlled test requests containing SQL injection-like patterns to evaluate WAF rule behavior.<br>- Review the Allowed and Blocked request metrics in AWS WAF. | 13/10/2026 | 14/10/2026 | [AWS WAF Documentation](https://docs.aws.amazon.com/waf/latest/developerguide/waf-metrics.html) |
| 5 | - Review AWS WAF request metrics and available logging configuration.<br>- Examine the results of the access tests.<br>- Summarize how AWS WAF helps protect the application endpoint behind the ALB.<br>- Collect screenshots and evidence for the security testing and evaluation stages. | 15/10/2026 | 16/10/2026 | [AWS WAF Documentation](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Week 9 Results:

- Understood the role of AWS WAF in protecting web applications from unwanted and potentially malicious requests.
- Reviewed the Web ACL configuration and verified its association with the Application Load Balancer.
- Learned how AWS WAF rules inspect incoming requests and apply allow or block actions.
- Performed basic request tests through the ALB endpoint.
- Reviewed the Allowed and Blocked request metrics to evaluate WAF behavior.
- Gained practical experience in using AWS WAF as an additional security layer for an AWS-hosted application.
- Collected monitoring information and test evidence for the overall security evaluation.