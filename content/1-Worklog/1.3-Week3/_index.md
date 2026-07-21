---
title: "Worklog Week 3"
date: 2026-05-26
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Practice provisioning and launching an Amazon EC2 Instance on the AWS cloud platform.
- Gain a clear understanding of EC2 core concepts, Subnet routing (Public vs. Private), and configuring secure access control for instances.

### Tasks Deployed This Week:

- **Theoretical Research:** Studied Amazon EC2 (Elastic Compute Cloud) fundamentals, including Instance Types, Amazon Machine Images (AMIs), and security mechanisms using Key Pairs and Security Groups.
- **Network Infrastructure Optimization:** Verified and adjusted VPC (Virtual Private Cloud) configurations, specifically enabling the `Auto-assign public IPv4 address` feature on the target Public Subnet to ensure Internet connectivity for upcoming instances.
- **EC2 Instance Deployment:** Executed the complete Launch Instance wizard: selected the appropriate AMI (Linux/Ubuntu), configured hardware resources (vCPU, RAM, EBS Storage), and generated a secure Key Pair for SSH access.
- **Firewall and Security Configuration:** Configured Inbound and Outbound rules within the Security Group to strictly manage and filter network traffic traveling to and from the instance.
- **Testing and Verification:** Conducted remote connectivity tests to the newly created EC2 instance via SSH/EC2 Instance Connect to verify system readiness and operational status.

### Week 3 Achievements & Results:

- **Successful Instance Provisioning:** Successfully deployed and launched an EC2 Instance running Linux/Ubuntu, maintaining a stable "Running" state within the designated VPC environment.
- **Subnet Configuration Mastery:** Successfully resolved IP assignment limitations by correctly enabling and verifying the `Auto-assign public IPv4` setting on the subnet, ensuring seamless status updates across the AWS Console.
- **Robust Security Implementation:** Established a secure remote access workflow by generating functional Key Pairs and defining optimized Security Group rules (opening specific ports such as Port 22 for SSH and Ports 80/443 for standard Web Traffic) to mitigate unauthorized access risks.
- **Enhanced Troubleshooting Skills:** Deepened hands-on experience with the AWS Management Console interface, mastered resource status monitoring, and successfully prepared the infrastructure for hosting practical cloud applications in the upcoming weeks.