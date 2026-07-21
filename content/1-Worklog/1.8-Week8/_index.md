---
title: "Worklog Week 8"
date: 2026-06-02
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Implement cloud data encryption mechanisms by provisioning customer-managed cryptographic assets.
* Construct a secure Amazon S3 infrastructure utilizing server-side encryption with AWS KMS (SSE-KMS) and validate object upload integrity.

### Tasks Implemented This Week:

* **AWS Key Management Service (KMS):** Deploy a Customer Managed Symmetric Key with active administrative boundaries and automatic annual key rotation rules enabled.
* **Amazon S3 Provisioning:** Remediate global naming conflicts to successfully initialize an isolated S3 bucket (`kms-key-s3-03072026`), customize object ownership profiles, and mitigate default public access constraints.
* **Data Ingestion & Cryptographic Enforcement:** Execute an object upload workflow using a sample asset (`klasjfhs.jpg`), explicitly configuring storage tiers, validating data integrity using explicit checksum algorithms, and enforcing targeted SSE-KMS default overrides.

### Week 8 Results:

#### 1. Initialized and Configured AWS Key Management Service (KMS)

* **Created Customer Managed Key:** Successfully executed the workflow to create a symmetric Customer Managed Key designed for cryptographic encryption and decryption operations, assigning it the alias `kms-key-encrypt-decrypt` (`image_f7d62b.png`, `image_f7dcee.png`).
* **Defined Privileges:** Designated administrative permissions to `kms-key-role` and generated the corresponding IAM key policy (`image_f7d92a.png`, `image_f7da02.png`).
* **Configured Key Rotation:** Enhanced the security posture of the cryptographic material by modifying the key rotation settings. Successfully enabled **Automatic Key Rotation** with a standard rotation frequency cycle of **365 days** (`image_f7dda7.png`, `image_f7e0ca.png`).

#### 2. Resolved Naming Conflicts & Provisioned S3 Bucket (`kms-key-s3-03072026`)

* **Error Remediation:** Encountered a standard `BucketAlreadyExists` conflict during global namespace checking (`image_f83ee3.png`). Resolved the error by appending a time-based unique suffix string (`03072026`).
* **Successful Initialization:** Successfully created the general-purpose bucket named **`kms-key-s3-03072026`** within the `sa-east-1` region (`image_f8424c.png`, `image_f84346.png`).
* **Security & Ingestion Settings:** Applied ACL write permissions, customized public visibility rules, and assigned default server-side encryption behaviors mapping to the unique customer-managed KMS key ARN.

#### 3. Secured Data Ingestion & Integrity Verification

* **Object Staging:** Initialized an upload workflow to store an asset named `klasjfhs.jpg` (14.9 KB) directly into the root level of the newly constructed bucket (`image_f84706.png`, `image_f84a8a.png`).
* **Storage Class Assignment:** Allocated the object to the **Standard storage class** to ensure high-availability and frequent access performance profiles across multiple Availability Zones (`image_f84abf.png`).
* **Explicit Encryption Override:** 
  * Instructed the upload engine to enforce server-side encryption parameters by selecting **"Specify an encryption key"** and choosing to **"Override bucket settings for default encryption"** (`image_f84ac8.png`).
  * Explicitly locked the target key to the newly deployed AWS KMS credential instance (ARN ending in `3609742e-1fff-452b-93b9-c0164008c405`) and kept the cost-saving **Bucket Key** optimization layer enabled (`image_f84ac8.png`, `image_f84d71.png`).
* **Integrity Validation:** Configured the optional verification boundary by applying the **CRC64NVME** checksum function to automatically compute and validate object structural integrity during the transport lifecycle (`image_f84d71.png`).
* **Execution Outcome:** Completed the operation with zero failures. The S3 console returned an explicit **"Upload succeeded"** state status confirmation message for the encrypted object (`image_f84d91.png`).