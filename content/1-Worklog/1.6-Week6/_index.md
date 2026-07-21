---
title: "Week 6 Worklog"
date: 2026-05-17
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---


### Week 6 Objectives:

* Gain hands-on experience with data protection and storage management within the AWS cloud environment.
* Successfully initialize Amazon S3 storage and configure necessary access control policies to prepare for the deployment of system backup plans.

### Tasks to be carried out this week:

* Create a globally unique Amazon S3 Bucket ensuring no naming conflicts within the global namespace.
* Construct a dedicated sub-folder hierarchy within the bucket for organized project asset storage.
* Upload required deployment templates and function packages to the target S3 path.
* Study and configure S3 access permissions, including Block Public Access toggles and JSON-based Bucket Policies.

### Week 6 Achievements:

* **Successful S3 Bucket Provisioning:** Successfully created a unique bucket named `backup-lab-02072026-xyz` located in the South America (São Paulo) region.
* **Structured Directory Implementation:** Established a clean storage structure by creating the `backup-lab/` sub-folder.
* **100% Asset Upload Success:** Successfully uploaded key deployment resources (`lambda_function.zip` and `backup-lab.yaml`) into the target folder with a 100% completion status (*Succeeded*).
* **Access Control Resolution:** Mastered the resolution of cloud security friction by properly handling conflicts between *Block all public access* settings and read-permission *Bucket Policies* (`s3:GetObject`).