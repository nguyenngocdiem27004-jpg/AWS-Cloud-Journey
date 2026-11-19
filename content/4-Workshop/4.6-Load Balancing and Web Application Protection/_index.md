---
title: "Load Balancing and Web Application Protection"
date: 2026-10-30
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

#### Overview

Application Load Balancer (ALB) and AWS Web Application Firewall (WAF) provide important layers of protection for web applications deployed on AWS.

In this project, the Application Load Balancer provides an entry point for HTTP traffic to the Nginx web server running on the private EC2 instance. AWS WAF is associated with the ALB to inspect incoming requests and filter potentially malicious web traffic.

### 1. Application Load Balancer

The project uses an Application Load Balancer named KLTN-ALB.

The ALB receives incoming HTTP requests and forwards eligible traffic to the configured target group.

To review the ALB configuration:

1. Open the **EC2** service.
2. Select **Load Balancers**.
3. Find KLTN-ALB.
4. Review its scheme, listeners, Availability Zones, and associated Security Group.
5. Open the associated target group.
6. Review the registered EC2 target and its health status.

The ALB provides a controlled access point to the web server instead of requiring users to connect directly to the private EC2 instance.

![KLTN-ALB configuration and status](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/alb-details.png)

![Target group and registered EC2 target health](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/target-group.png)

### 2. AWS WAF Configuration

AWS WAF is used to inspect HTTP requests and apply web traffic filtering rules.

The project uses a Web ACL named KLTN-WebACL, which is associated with KLTN-ALB.

To review the Web ACL:

1. Open the **AWS WAF & Shield** service.
2. Select **Web ACLs**.
3. Find KLTN-WebACL.
4. Review its associated AWS resource.
5. Inspect the configured rules and rule groups.
6. Review the available traffic metrics.

AWS Managed Rules can help detect and block common web attack patterns, including SQL injection and cross-site scripting attempts.

![KLTN-WebACL associated with the Application Load Balancer](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-web-acl.png)

![AWS WAF managed rule configuration](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-rules.png)

### 3. Web Traffic Verification

The project performs basic HTTP request tests to observe how the web application responds before and after WAF protection is applied.

The tests include:

- Normal HTTP requests to verify that the web service remains accessible.

- SQL injection patterns in request parameters.

- Cross-site scripting (XSS) patterns in request parameters.

- Path traversal-style requests.

Example test commands:

```bash
curl -i "http://<ALB-DNS>/"
```

SQL injection pattern:

```bash
curl -i "http://<ALB-DNS>/?id=1%20OR%201=1"
```

XSS pattern:

```bash
curl -i "http://<ALB-DNS>/?input=<script>alert(1)</script>"
```

Replace <ALB-DNS> with the actual DNS name of the Application Load Balancer.

![Normal HTTP request returning HTTP 200](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-normal-request.png)

### 4. Test Results

During the implementation, the normal web request was successfully served by the web server.

The security tests produced the following observed results:

| Test | Observed Result |
|---|---|
| Normal HTTP request | HTTP 200 |
| SQL injection test before WAF protection | HTTP 200 |
| SQL injection test after WAF protection | HTTP 403 |
| XSS test before WAF protection | HTTP 200 |
| XSS test after WAF protection | HTTP 403 |
| Path traversal-style request | HTTP 400 |

The HTTP 403 responses observed during the SQL injection and XSS tests indicate that the requests were blocked by the configured web protection layer.

The HTTP 400 response for the path traversal-style request indicates that the request was rejected. This result should not be interpreted as proof that AWS WAF specifically blocked it unless the corresponding WAF log or metric confirms the rule action.

![SQL injection and XSS test requests returning HTTP 403](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-sqli-xss.png)

![AWS WAF sampled request showing a blocked SQL injection request](/images/4-Workshop/4.6-Load%20Balancing%20and%20Web%20Application%20Protection/waf-sampled-block.png)

### 5. Security Benefits

The ALB and WAF configuration provides the following benefits:

- Centralized entry point for incoming web traffic.

- Separation between the public-facing load balancer and private EC2 server.

- Inspection of incoming HTTP requests.

- Filtering of requests matching configured web attack rules.

- Reduced direct exposure of the application server.

### 6. Conclusion

This section demonstrates how Application Load Balancer and AWS WAF work together to provide web access and traffic protection.

The practical tests show that SQL injection and XSS test requests received HTTP 403 responses after WAF protection was applied, while normal web access continued to return HTTP 200.

