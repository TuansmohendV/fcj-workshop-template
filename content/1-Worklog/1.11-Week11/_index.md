---
title: "Week 11 Worklog"
date: 2026-07-11
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---


### Week 11 Objectives:
* Initialize the storage layer infrastructure on Amazon S3 to serve as the project's Data Lake.
* Establish a structured directory layout for storing different tiers of data.
* Populate the initial reference metadata required for downstream data processing.

### Tasks to Implement This Week:
*  Create a new Amazon S3 bucket designated as the centralized Data Lake storage.
*  Construct a standard directory structure (`data/` and `reference_data/`) inside the bucket.
*  Upload initial dataset schema/metadata definitions into the reference directory.

### Achievements in Week 11:

#### 1. Data Lake Bucket Initialization
* **Bucket Name:** `asg-datalake-tuan-2026`
* **Region:** South America (São Paulo) `sa-east-1`
* **Status:** Successfully provisioned with standard private access settings.

#### 2. Directory Structure Setup
Two main logical folders were created within the bucket to segregate different data types:
* `data/`: Dedicated directory for raw and incoming operational datasets.
* `reference_data/`: Dedicated directory for static lookup tables, configurations, and metadata files.

#### 3. Data Ingestion & Storage Loading
* **Target Destination:** `s3://asg-datalake-tuan-2026/reference_data/`
* **Uploaded File:** `tracks_list.json` (Size: 8.7 KB, Type: `application/json`)
* **Upload Status:** 100% Succeeded with 0 errors.

### Evaluation:
*  Successfully deployed the storage architecture layer on Amazon S3.
*  Verified data integrity through a successful initial JSON file ingestion.
*  The storage environment is fully prepared for future integration with data crawlers and analytics services.

