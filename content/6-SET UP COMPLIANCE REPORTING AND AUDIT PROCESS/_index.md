---
title : "Set Up Compliance Reporting And Audit Process"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

### Query CloudTrail Logs with CloudWatch Logs Insights
Purpose: Filter DeleteObject, DeleteBucket, RestoreObject events for testing.
### Set up Compliance Reporting
Purpose: Periodically export reports on deletion and recovery actions on the S3 system.
1. Go to CloudWatch > Logs Insights.
![CloudWatch logs](1.png)
![CloudWatch logs](2.png)
2. Select the log group containing CloudTrail logs
![CloudWatch logs](3.png)
3. Paste the following query:
```
fields @timestamp, eventName, userIdentity.userName, requestParameters.bucketName, sourceIPAddress
| filter eventSource = "s3.amazonaws.com"
  and eventName in ["DeleteObject", "DeleteBucket", "RestoreObject"]
| sort @timestamp desc
| limit 50
```
1. Click **Run query**.
![CloudWatch logs](4.png)
![CloudWatch logs](5.png)
**Result: Displays the most recent DeleteObject, DeleteBucket, RestoreObject actions.**
### Audit Procedures
After running the Logs Insights query:
1. Click Export results > Download CSV.
![CloudWatch logs](6.png)
1. Save as file and open it by Excel.
![CloudWatch logs](7.png)

### Cost Analysis
1. Select **Cost Explorer**
![Cost Analysis](Cost-Explorer-1.png)
![Cost Analysis](Cost-Explorer-2.png)
2. Filter: You can filter by attributes
- Date Range
- Granularity
- Dimension
- Service
- Linked account
- Region
- ...
![Cost Analysis](Cost-Explorer-3.png)
3. Export results (CSV or PDF) to include in reports.
![Cost Analysis](Cost-Explorer-4.png)