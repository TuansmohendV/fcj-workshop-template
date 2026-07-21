---
title: "Worklog Week 7"
date: 2026-06-17
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Research and implement Identity and Access Management (IAM) solutions combined with data encryption mechanisms for cloud storage on AWS.
* Construct a secure, least-privilege permission structure for user groups and Amazon S3 storage services.

### Tasks Implemented This Week:

* **Identity and Access Management (IAM):** Configure Customer Managed Policies, Service IAM Roles, IAM Users, and IAM User Groups via the AWS Management Console.
* **Data Encryption (KMS):** Initialize and configure an AWS KMS Customer Managed Symmetric Key to prepare for default server-side encryption on S3 Buckets.

### Week 7 Results:

#### 1. Completed Identity and Access Management (IAM) Setup

* **Created Custom Policy & Role:** Successfully initialized `kms-key-policy` and attached it to a new IAM Role named `kms-key-role`. Configured the Trust Relationship to allow the Amazon S3 service (`s3.amazonaws.com`) to assume this role.
* **Managed User Groups:** Created an IAM User Group named `GroupLimit` and attached the AWS-managed policy `AmazonS3FullAccess` to regulate storage resource access.
* **Managed IAM Users:** 
  * Successfully created a new IAM User named `User-S34` and enabled AWS Management Console access with a custom password.
  * Assigned `User-S34` to the `GroupLimit` group to inherit group permissions.
  * Exported the login credentials file (`credentials.csv`) and verified successful authentication into the AWS Console using the new identity.

#### 2. Initialized and Configured AWS Key Management Service (KMS)

* Executed the configuration workflow for a Customer Managed Symmetric Key.
* Defined Key Administrative privileges for the current administrator account and assigned Key Usage Permissions to `kms-key-role`, enabling Amazon S3 to utilize the key for cryptographic operations (encryption/decryption).