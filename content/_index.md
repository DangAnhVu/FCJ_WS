---
title : "Data Archival và Compliance với Glacier và Vault Lock"
weight : 1 
chapter : false
---

# Data Archival và Compliance với Glacier và Vault Lock

#### Overview
Implement a compliant and automated data archival system using Amazon S3 Glacier and Vault Lock to meet legal and regulatory requirements. The system should support:
- Cost-effective long-term data storage.
- Immutable Vault Lock policies to ensure regulatory compliance.
- Retrieval optimization from S3 Glacier.
- Generation of audit, cost, and compliance reports.
- Legal hold mechanisms to preserve data under investigation.

#### Overview of Implementation Steps
1. **Design a compliance framework architecture.**
2. **Create S3 buckets with versioning, Object Lock, and encryption enabled.**
3. **Define lifecycle policies to automatically transition data to S3 Glacier/Deep Archive.**
4. **Enable immutable Vault Lock policies to enforce compliance.**
5. **Configure CloudTrail and CloudWatch for monitoring and auditing.**
6. **Integrate EventBridge + SNS to notify unusual behaviors.**
7. **Generate storage cost and retrieval optimization reports.**
8. **Implement Legal Hold procedures to prevent deletion during investigations.**

#### Amazon S3
- Primary storage for objects.
- Versioning and Object Lock support compliance and legal hold requirements.
- Uses bucket policies and IAM for access control.
![Amazon S3](/images/1/AWSS3.png)

#### Amazon S3 Glacier / Glacier Deep Archive
- Cost-effective long-term storage.
- Supports Vault Lock for write-once-read-many (WORM) compliance policies.
- Offers multiple retrieval tiers (expedited, standard, bulk).
![Amazon S3 Glacier](/images/1/S3%20Glacier.PNG)

#### S3 Glacier Vault Lock
- Enforces compliance by locking vault policies after a test period.
- Complies with regulations like SEC Rule 17a-4(f), FINRA, HIPAA, etc.

#### AWS CloudTrail
- Records all API activities and user actions across AWS resources.
- Essential for building an audit trail.
![Amazon CloudTrail](/images/1/AWSCloudTrail.png)

#### Amazon CloudWatch
- Monitors logs and metrics.
- Generates alerts on unusual behavior and provides dashboard monitoring.
![AmazonCloudWatch](/images/1/AWSCloudWatch.png)

#### AWS EventBridge + SNS
- EventBridge detects events like deletions or policy changes.
![Amazon EventBridge](/images/1/S3EventBridge.png)
- SNS sends notifications via email or other monitoring tools.
![Amazon SNS](/images/1/SNS.png)

#### AWS Config (optional)
- Tracks configuration changes of AWS resources.
- Evaluates resource compliance over time.

#### AWS Cost Explorer / S3 Storage Lens
- Analyzes storage and retrieval costs.
- Identifies opportunities to optimize storage expenses.

Customers who choose AWS Support gain one-on-one, fast-response support from AWS engineers. The service helps customers use AWS's products and features. With pay-by-the-month pricing and unlimited support cases, customers are freed from long-term commitments. Customers with operational issues or technical questions can contact a team of support engineers and receive predictable response times and personalized support.


#### Main Content

1. [Create the Source S3 Bucket](1-Create%20the%20Source%20S3%20Bucket/)
2. [Create Glacier Vault and configure Vault Lock Policy](2-Create%20S3%20Glacier%20Vault/)
3. [Set up S3 Lifecycle Policy – Automatically move data from S3 to Glaciers](3-Set%20up%20Vault%20Lock%20Policy/)
4. [Implement Monitoring, Auditing and Compliance Reporting](4-%20Implement%20Monitoring,%20Auditing%20and%20Compliance%20Reporting/)
5. [Testing The Waning System](5-TESTING%20THE%20WARNING%20SYSTEM/)
6. [Set Up Compliance Reporting And Audit Process](6-SET%20UP%20COMPLIANCE%20REPORTING%20AND%20AUDIT%20PROCESS/)
7. [Clean Up Resources](7-Clean%20Resource/)