---
title: "Week 10 Worklog"
date: 2026-07-05
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---


### Week 10 Objectives:

* Configure and manage system permissions on AWS IAM (Identity and Access Management) dedicated to AWS Glue services.
* Ensure AWS Glue is granted comprehensive access to S3 resources and execution permissions (`iam:PassRole`) safely following the principle of least privilege.

### Tasks to Implement This Week:

*  Create a new IAM Role specifically for AWS Glue.
*  Attach required AWS Managed Policies, including full S3 access and core Glue service permissions.
*  Create a Custom IAM Policy to manage the `iam:PassRole` permission.
*  Attach the Custom Policy to the newly created IAM Role to complete the authorization workflow.

### Achievements in Week 10:

#### 1. IAM Role Configuration Details (`AWSGlueServiceRoleDefault`)
* **ARN:** `arn:aws:iam::150460248067:role/AWSGlueServiceRoleDefault`
* **Creation Date:** July 04, 2026, 01:31 (UTC+07:00)
* **Maximum Session Duration:** 1 hour
* **Trusted Entity:** AWS Service (`glue.amazonaws.com`)

#### 2. Attached Permissions Policies (3 policies)

The role's permission structure has been successfully configured using 3 specific policies:
* **`AmazonS3FullAccess`** *(AWS managed)*: Grants full data operation access (Read/Write) across Amazon S3 buckets.
* **`AWSGlueServiceRole`** *(AWS managed)*: Provides the default essential permissions for the AWS Glue service to execute Crawlers and ETL Jobs.
* **`milo`** *(Customer managed)*: A custom JSON policy designed to delegate `iam:PassRole` capability to this specific role instance:
  ```json
  {
      "Version": "2012-10-17",
      "Statement": [
          {
              "Sid": "Statement1",
              "Effect": "Allow",
              "Action": "iam:PassRole",
              "Resource": "arn:aws:iam::150460248067:role/AWSGlueServiceRoleDefault"
          }
      ]
  }

