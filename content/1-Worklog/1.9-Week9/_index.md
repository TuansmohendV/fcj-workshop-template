---
title: "Week 9 Worklog"
date: 2026-06-20
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

* Establish an automated auditing and logging system for activities on the AWS Cloud infrastructure.
* Configure centralized storage for AWS CloudTrail logs into Amazon S3 to prepare for advanced data analysis using Amazon Athena.

### Tasks to Implement This Week:

* **Initialize AWS CloudTrail:** Create a new Multi-region trail to monitor and audit all API activities across the AWS account.
* **Configure Amazon S3 Integration:** Set up the log file destination to point directly to the existing S3 Bucket `kms-key-s3-03072026`.
* **Configure Log Event Filtering:** Detail event filters to capture both administrative operations (Management events) and data modifications within the bucket (Data events).

### Week 9 Achievements:

#### 1. Routing and Initializing AWS CloudTrail
* **Service Navigation:** Successfully used the AWS Console search bar to navigate from the Amazon S3 interface to the **CloudTrail** central management console (`image_f8604f.png`).
* **Starting the Workflow:** Accessed the **Trails** section in the left navigation pane and selected **Create trail** to begin the setup (`image_f860b2.png`).

#### 2. Configuring Trail Attributes (Choose Trail Attributes)

* **Defining Trail Name:** Set the unique trail identifier name as `kms-key-cloudtrail` for structured management (`image_f8b302.png`).
* **Centralized S3 Storage:** 
  * Selected the **"Use existing S3 bucket"** option to optimize pre-existing storage resources (`image_f8b302.png`).
  * Entered the exact target S3 Bucket name: `kms-key-s3-03072026` (`image_f8b302.png`).
* **Securing Log Files with Encryption:** 
  * Kích hoạt the **Log file SSE-KMS encryption** feature (`image_f8b302.png`).
  * Selected **New** under the Customer managed AWS KMS key section and defined the AWS KMS alias for the new log encryption key as `cloudtrail` (`image_f8b387.png`).
* **Additional Settings:** Enabled **Log file validation** to ensure log file integrity and protect against unauthorized tampering or modifications (`image_f8b323.png` / `image_f8b387.png`).

#### 3. Configuring Log Event Filters (Choose Log Events)

* **Enabling Management Events:** Configured the trail to record all administrative infrastructure operations, including both **Read** and **Write** API activities (`image_f8b3c5.png`).
* **Enabling S3 Data Events:** 
  * Specified the data event source type explicitly as **S3** (`image_f8b701.png`).
  * Under the **Individual bucket selection**, assigned the S3 Bucket `kms-key-s3-03072026` to the monitoring list to capture all **Read** and **Write** operations performed on objects inside it (`image_f8b701.png`).

#### 4. Final Review Before Deployment (Review and Create)

* **Reviewing Trail Attributes:** Verified all core parameters summary, including Multi-region: *Yes*, SSE-KMS encryption with the key `cloudtrail`: *Enabled*, and the log location correctly mapped to `kms-key-s3-03072026/AWSLogs/150460248067/` (`image_f8b70a.png`).
* **Reviewing Log Event Filters:** Confirmed that the filters include all Management events (API activity: All) (`image_f8ba6e.png`). Verified that logging (Read/Write) for object-level actions within the specific S3 Bucket `kms-key-s3-03072026` is fully enabled (`image_f8bae8.png`).
* Advanced configurations such as *Insights events*, *Network activity events*, and *Configure event aggregation* were kept at their default disabled states (`image_f8ba6e.png` / `image_f8bae8.png`).

#### 5. Completion and Operational Status

* **Successful Initialization:** Upon clicking create, the system displayed a green confirmation banner stating **"Trail successfully created"** on the main dashboard (`image_f8bb44.png`).
* **Operational Status:** 
  * The `kms-key-cloudtrail` trail, with its home region set to **South America (São Paulo)**, is now officially active (`image_f8bb44.png`).
  * The **Multi-region trail** property displays *Yes*, and the **Status** column shows a green checkmark indicating **Logging** in real-time (`image_f8bb44.png`).
  * All generated log data is now being automatically partitioned and delivered directly to the destination S3 bucket `kms-key-s3-03072026` (`image_f8bb44.png`).