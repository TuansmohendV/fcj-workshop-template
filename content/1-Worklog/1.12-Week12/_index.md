---
title: "Week 12 Worklog"
date: 2026-07-17
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---


### Week 12 Objectives:
* Implement an event-driven serverless architecture using AWS Lambda to handle automated image processing.
* Utilize AWS Cloud9 IDE to develop, package, and deploy the serverless source code.
* Configure S3 Event Notifications to automatically trigger the Lambda function upon new image uploads.

### Tasks to Implement This Week:
*  Initialize an AWS Cloud9 environment for serverless development.
*  Create an AWS Lambda function (`CreateThumbnail`) with a Node.js runtime environment.
*  Set up an Amazon S3 Bucket Event Notification trigger to capture `ObjectCreated` events.
*  Troubleshoot and resolve the module syntax error (`Runtime.UserCodeSyntaxError`) during local integration testing.

### Achievements in Week 12:

#### 1. Serverless Lambda Function Initialization
* **Function Name:** `CreateThumbnail`
* **Runtime:** Node.js 18.x (Architecture: `x86_64`)
* **Deployment Method:** Developed and packaged via AWS Cloud9 workspace environment.

#### 2. Troubleshooting & Technical Resolutions
* **Issue Encountered:** During initial execution testing, the Lambda function threw a `Runtime.UserCodeSyntaxError: Cannot use import statement outside a module`. This occurred because the script used ES Module syntax (`import`) while Node.js defaulted to CommonJS execution rules.
* **Resolution Implemented:** Successfully modified the `package.json` configuration file inside the Cloud9 workspace by adding the `"type": "module"` property. Re-packaged and deployed the function deployment package via the command line.

#### 3. S3 Trigger Event Configuration
* **Source Bucket:** `asg-datalake-tuan-2026`
* **Event Type:** `All object create events` (`s3:ObjectCreated:*`)
* **Mechanism:** Verified the automation hook; any image uploaded to the source directory now triggers the Lambda thumbnail execution flow seamlessly.

### Evaluation:
*  100% completed establishing the automated image processing pipeline using AWS Cloud9 and Lambda.
*  Successfully resolved the runtime module compilation error, ensuring robust ES Module execution compatibility.
*  The system is operating securely, responding to real-time S3 events with zero infrastructure management overhead.

