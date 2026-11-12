---
title: "Worklog Week 7"
date: 2026-09-26
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

- Learn the process of deploying a web server on Amazon EC2.
- Install and configure Nginx on an Ubuntu Server instance.
- Configure Security Groups to control HTTP traffic between the Application Load Balancer and the EC2 instance.
- Configure an Application Load Balancer to forward incoming HTTP requests to the web server.
- Test website accessibility through the Application Load Balancer DNS name.
- Prepare the web server environment for implementing additional security and monitoring services in the following weeks.

### Tasks to Be Implemented This Week:

| Day | Tasks | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| 2 | - Check the EC2 instance status and network configuration implemented in previous weeks.<br>- Review the operating system, private IP address, and Security Group settings of the server.<br>- Learn about Nginx and its role as a web server in the AWS infrastructure.<br>- Prepare the EC2 environment for installing the web service. | 26/09/2026 | 26/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Update the software package list on Ubuntu Server.<br>- Install Nginx on the EC2 instance.<br>- Check the Nginx service status and configure it to start automatically when the system boots.<br>- Verify that the web service is listening on the required port. | 27/09/2026 | 28/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 4 | - Review and configure Security Group rules for the web server.<br>- Allow HTTP traffic through TCP port 80 from the Application Load Balancer Security Group.<br>- Review the communication rules between the ALB and EC2 instance.<br>- Configure the ALB listener and target group to forward HTTP requests to the EC2 instance.<br>- Check the target group health status. | 29/09/2026 | 30/09/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 5 | - Access the web server through the Application Load Balancer DNS name.<br>- Check the Nginx service status and troubleshoot access errors if necessary.<br>- Verify the ALB listener, target group, health check, and Security Group configuration.<br>- Record the website access test results and prepare for implementing security and monitoring services in Week 8. | 01/10/2026 | 02/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

### Week 7 Results:

- Understood the process of deploying a web server on Amazon EC2.
- Installed Nginx on the Ubuntu Server instance.
- Checked the Nginx service status and verified that the web service was running.
- Configured Security Group rules to allow HTTP traffic from the Application Load Balancer to the EC2 instance.
- Learned how to configure an ALB listener and target group to distribute incoming HTTP requests.
- Checked the target group health status and verified that the EC2 instance was healthy.
- Successfully accessed the Nginx welcome page through the Application Load Balancer DNS name.
- Established a working web server environment for implementing additional security and monitoring services in the following weeks.