---
title: "AWS WAF Configuration and Web Traffic Filtering"
date: 2026-10-30
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

#### Overview

This section describes the configuration of AWS Web Application Firewall (AWS WAF) to help protect the web application infrastructure deployed on AWS.

AWS WAF is associated with the Application Load Balancer (ALB) to inspect incoming HTTP requests and apply configured web access rules.

In this project, the Web ACL named `KLTN-WebACL` is associated with `KLTN-ALB`. The purpose is to control incoming web traffic and demonstrate how AWS WAF can allow or block requests based on configured rules.

#### 1. Prepare the WAF Environment

Before configuring AWS WAF, verify that the following resources are available:

- An existing Application Load Balancer named `KLTN-ALB`.
- An AWS WAF Web ACL named `KLTN-WebACL`.
- A web server running behind the Application Load Balancer.
- Access to the AWS Management Console.

The Application Load Balancer provides the entry point for incoming web traffic, while AWS WAF inspects requests before they reach the web server.

#### 2. Create and Configure a Web ACL

To configure AWS WAF:

1. Open the AWS Management Console.
2. Navigate to **AWS WAF & Shield**.
3. Select **Web ACLs**.
4. Open the Web ACL named `KLTN-WebACL`.
5. Review its configured rules and default action.
6. Check the associated AWS resource.

A Web ACL contains rules that determine whether incoming requests should be allowed or blocked.

#### 3. Associate AWS WAF with the Application Load Balancer

AWS WAF is associated with the Application Load Balancer to inspect incoming HTTP requests.

Verify the association as follows:

1. Open the AWS WAF console.
2. Select `KLTN-WebACL`.
3. Review the associated AWS resources.
4. Confirm that `KLTN-ALB` is listed.

This configuration allows AWS WAF to inspect web requests before they are forwarded to the EC2 web server.

#### 4. Review Web Traffic Filtering

After associating the Web ACL with the Application Load Balancer, review the request statistics in the AWS WAF console.

The dashboard provides information about requests that were allowed or blocked by the configured rules.

During the implementation, the Web ACL dashboard displayed the following results:

| Request action | Number of requests |
|---|---:|
| Allowed | 5 |
| Blocked | 25 |
| Total | 30 |

These results demonstrate that AWS WAF processed incoming requests and applied its traffic filtering rules.

#### 5. Verify the WAF Configuration

To verify the configuration:

1. Open the AWS WAF console.
2. Select `KLTN-WebACL`.
3. Check the associated resource and confirm that `KLTN-ALB` is attached.
4. Review the request statistics.
5. Compare the allowed and blocked request counts.

The ALB can also be accessed through its DNS name to verify that the web server is reachable.

**Note:** The request statistics demonstrate that AWS WAF processed and filtered traffic. They should not be interpreted as proof that every individual attack type has been tested unless corresponding test results are available.

#### Conclusion

In this section, AWS WAF was configured and associated with the Application Load Balancer to inspect incoming web traffic.

The recorded statistics showed 30 processed requests, including 5 allowed requests and 25 blocked requests. This demonstrates how AWS WAF can provide an additional layer of protection for web infrastructure deployed on AWS.