---
title : "Implement Monitoring, Auditing and Compliance Reporting"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

### Implement Monitoring, Auditing and Compliance Reporting

#### Enable AWS CloudTrail

1. Search **AWS CloudTrail** on AWS Console, Select **CloudTrail**
![CloudTrail](CloudTrail-1.png)
2. Select Trails, select **Create Trail**
![CloudTrail](CloudTrail-2.png)
3. Configuration:
- Trail name: `Trail name`
- Storage location: **Create new S3 bucket**
- Log file SSE-KMS encryption: **Enable**
- Customer managed AWS KMS key: **New**, AWS KMS alias: `archival-compliance-trail-key`
- Log file validation: **Enable**
- CloudWatch Logs - optional
  - CloudWatch Logs: **Enable**
  - Log group: **New**, Log group name: `aws-cloudtrail-logs-ws-< YourID >-1613c3f0`
![CloudTrail](CloudTrail-3.png)
![CloudTrail](CloudTrail-4.png)
- Select **Next**
- Choose log events
  - Events: tick on **Management events**, **Data events**
  - Management events: tick on **Read**, **Write**
![CloudTrail](CloudTrail-5.png)
![CloudTrail](CloudTrail-6.png)
- Select **Next**
- Review and **Create trail**
![CloudTrail](CloudTrail-7.png)
#### Configure AWS CloudWatch Monitoring
##### Create Metric Filter
1. Search **AWS CloudWatch** on AWS Console, Select **CloudWatch**
![CloudWatch](CloudWatch-1.png)
2. Select the log group containing the CloudTrail logs just created.
![CloudWatch](CloudWatch-2.png)
3. **Create Metric Filter**
![CloudWatch](CloudWatch-3.png)
4. Configuration for DeleteObject: 
- Filter pattern: `{ $.eventName = "DeleteObject" }`
![CloudWatch](CloudWatch-4.png)
- Select **Next**
- **Assign metric**
  - Filter name: `DeleteObjectEventMetricFilter`
  - Metric namespace: `S3/DeleteObjectMonitoring`
  - Metric name: `DeleteObjectEventCount`
  - Metric value: `1`
  - Default value: blank
  - Unit: **Count**
![CloudWatch](CloudWatch-5.png)
![CloudWatch](CloudWatch-6.png)
- Select **Next**
- Review and Create
![CloudWatch](CloudWatch-7.png)
![CloudWatch](CloudWatch-8.png)

1. Do the same with **DeleteBucket**
![CloudWatch](CloudWatch-19.png)
![CloudWatch](CloudWatch-20.png)
![CloudWatch](CloudWatch-21.png)
![CloudWatch](CloudWatch-22.png)
![CloudWatch](CloudWatch-23.png)
1. Do the same with **RestoreObject**
![CloudWatch](CloudWatch-24.png)
![CloudWatch](CloudWatch-25.png)
![CloudWatch](CloudWatch-26.png)
![CloudWatch](CloudWatch-27.png)
![CloudWatch](CloudWatch-28.png)

##### Create CloudWatch Alarm
1. Create Cloud Alarm for event **DeleteObject**
- Select that metric filter
![CloudWatch](CloudWatch-9.png)
- Specify metric and conditions
 - Threshold type: **Static**
 - Whenever DeleteObjectEventCount is...: **Greater**
 - than: **1**
- Select **Next**
![CloudWatch](CloudWatch-10.png)
![CloudWatch](CloudWatch-11.png)
- Configure actions:
 - Alarm state trigger: **In Alarm**
 - Send a notification to the following SNS topic: **Create new topic**
   - Topic name: `S3_DeleteObject_Alarm_Topic`
   - Email endpoint: `< Your email >`
![CloudWatch](CloudWatch-12.png)
   - **Create Topic** and Confirm your email via gmail 
![CloudWatch](CloudWatch-13.png)
![CloudWatch](CloudWatch-14.png)
   - Select **Next**  
 - Add alarm details:
   - Alarm name: `S3-DeleteObject-Alarm`
   - Alarm description: `# Track object deletion events on S3`
   - Select **Next**
![CloudWatch](CloudWatch-15.png)
 - Review and Create:
![CloudWatch](CloudWatch-16.png)
![CloudWatch](CloudWatch-17.png)
![CloudWatch](CloudWatch-18.png)
2. Create Cloud Alarm for event **DeleteBucket**
![CloudWatch](CloudWatch-29.png)
![CloudWatch](CloudWatch-30.png)
![CloudWatch](CloudWatch-31.png)
![CloudWatch](CloudWatch-32.png)
![CloudWatch](CloudWatch-33.png)
![CloudWatch](CloudWatch-34.png)
![CloudWatch](CloudWatch-35.png)
![CloudWatch](CloudWatch-36.png)
3. Create Cloud Alarm for event **RestoreObject**
![CloudWatch](CloudWatch-37.png)
![CloudWatch](CloudWatch-38.png)
![CloudWatch](CloudWatch-39.png)
![CloudWatch](CloudWatch-40.png)
![CloudWatch](CloudWatch-41.png)
![CloudWatch](CloudWatch-42.png)
![CloudWatch](CloudWatch-43.png)
