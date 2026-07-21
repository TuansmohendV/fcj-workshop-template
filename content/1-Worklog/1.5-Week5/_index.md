---
title: "Week 5 Worklog"
date: 2026-06-05
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Objectives for Week 5:
* Initialize a secure VPC network infrastructure for the application.
* Deploy a MySQL database (RDS) and a trạm làm việc (EC2 Windows Host).
* Automate the development environment setup and seed initial sample data.

### Tasks to Deploy This Week:
* Deploy the CloudFormation template to create the VPC, Subnets, NAT Gateways, and IAM Roles.
* Provision an RDS MySQL instance within the isolated Private Subnets.
* Configure the EC2 Windows Host to run bootstrap scripts for installing tools (Java, Maven, Tomcat, IDEs).
* Execute the SQL script to initialize the database schema and mock data for the TravelBuddy application.

### Achievements for Week 5:
* **Networking (VPC):** Successfully created `DevAxNetworkVPC` consisting of 2 Public Subnets and 2 Private Subnets, pre-configured with NAT Gateways for secure internal routing.
* **Database (RDS):** Deployed a MySQL 8.0 instance (`db.t2.micro`) securely nested inside the Private Subnets.
* **Server (EC2 Windows):** Successfully launched the Windows Server 2019 instance, automatically installing the full development suite (Java, Maven, Git, Tomcat, Eclipse, IntelliJ) via bootstrap scripts.
* **Sample Data:** Executed the `DB.sql` script to generate core tables (`flightspecial`, `hotelspecial`) and populate mock data for TravelBuddy.
* **Security:** Configured Security Groups to open necessary ports for RDP (3389) and MySQL (3306), and established required system IAM Roles.