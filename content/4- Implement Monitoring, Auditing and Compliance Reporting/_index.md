---
title : "Implement Monitoring, Auditing and Compliance Reporting"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

### Implement Monitoring, Auditing and Compliance Reporting

#### Enable AWS CloudTrail

1. Search **AWS CloudTrail** on AWS Console, Select **CloudTrail**
![CloudTrail](/images/4//CloudTrail-1.png)
2. Select Trails, select **Create Trail**
![CloudTrail](/images/4//CloudTrail-2.png)
3. Configuration:
- Trail name: `Trail name`
- Storage location: **Create new S3 bucket**
- Log file SSE-KMS encryption: **Enable**
- Customer managed AWS KMS key: **New**, AWS KMS alias: `archival-compliance-trail-key`
- Log file validation: **Enable**
- CloudWatch Logs - optional
  - CloudWatch Logs: **Enable**
  - Log group: **New**, Log group name: `aws-cloudtrail-logs-ws-< YourID >-1613c3f0`
![CloudTrail](/images/4//CloudTrail-3.png)
![CloudTrail](/images/4//CloudTrail-4.png)
- Select **Next**
- Choose log events
  - Events: tick on **Management events**, **Data events**
  - Management events: tick on **Read**, **Write**
![CloudTrail](/images/4//CloudTrail-5.png)
![CloudTrail](/images/4//CloudTrail-6.png)
- Select **Next**
- Review and **Create trail**
![CloudTrail](/images/4//CloudTrail-7.png)
#### Configure AWS CloudWatch Monitoring
##### Create Metric Filter
1. Search **AWS CloudWatch** on AWS Console, Select **CloudWatch**
![CloudWatch](/images/4//CloudWatch-1.png)
2. Select the log group containing the CloudTrail logs just created.
![CloudWatch](/images/4//CloudWatch-2.png)
3. **Create Metric Filter**
![CloudWatch](/images/4//CloudWatch-3.png)
4. Configuration for DeleteObject: 
- Filter pattern: `{ $.eventName = "DeleteObject" }`
![CloudWatch](/images/4//CloudWatch-4.png)
- Select **Next**
- **Assign metric**
  - Filter name: `DeleteObjectEventMetricFilter`
  - Metric namespace: `S3/DeleteObjectMonitoring`
  - Metric name: `DeleteObjectEventCount`
  - Metric value: `1`
  - Default value: blank
  - Unit: **Count**
![CloudWatch](/images/4//CloudWatch-5.png)
![CloudWatch](/images/4//CloudWatch-6.png)
- Select **Next**
- Review and Create
![CloudWatch](/images/4//CloudWatch-7.png)
![CloudWatch](/images/4//CloudWatch-8.png)

1. Do the same with **DeleteBucket**
![CloudWatch](/images/4//CloudWatch-19.png)
![CloudWatch](/images/4//CloudWatch-20.png)
![CloudWatch](/images/4//CloudWatch-21.png)
![CloudWatch](/images/4//CloudWatch-22.png)
![CloudWatch](/images/4//CloudWatch-23.png)
1. Do the same with **RestoreObject**
![CloudWatch](/images/4//CloudWatch-24.png)
![CloudWatch](/images/4//CloudWatch-25.png)
![CloudWatch](/images/4//CloudWatch-26.png)
![CloudWatch](/images/4//CloudWatch-27.png)
![CloudWatch](/images/4//CloudWatch-28.png)

##### Create CloudWatch Alarm
1. Create Cloud Alarm for event **DeleteObject**
- Select that metric filter
![CloudWatch](/images/4//CloudWatch-9.png)
- Specify metric and conditions
 - Threshold type: **Static**
 - Whenever DeleteObjectEventCount is...: **Greater**
 - than: **1**
- Select **Next**
![CloudWatch](/images/4//CloudWatch-10.png)
![CloudWatch](/images/4//CloudWatch-11.png)
- Configure actions:
 - Alarm state trigger: **In Alarm**
 - Send a notification to the following SNS topic: **Create new topic**
   - Topic name: `S3_DeleteObject_Alarm_Topic`
   - Email endpoint: `< Your email >`
![CloudWatch](/images/4//CloudWatch-12.png)
   - **Create Topic** and Confirm your email via gmail 
![CloudWatch](/images/4//CloudWatch-13.png)
![CloudWatch](/images/4//CloudWatch-14.png)
   - Select **Next**  
 - Add alarm details:
   - Alarm name: `S3-DeleteObject-Alarm`
   - Alarm description: `# Track object deletion events on S3`
   - Select **Next**
![CloudWatch](/images/4//CloudWatch-15.png)
 - Review and Create:
![CloudWatch](/images/4//CloudWatch-16.png)
![CloudWatch](/images/4//CloudWatch-17.png)
![CloudWatch](/images/4//CloudWatch-18.png)
2. Create Cloud Alarm for event **DeleteBucket**
![CloudWatch](/images/4//CloudWatch-29.png)
![CloudWatch](/images/4//CloudWatch-30.png)
![CloudWatch](/images/4//CloudWatch-31.png)
![CloudWatch](/images/4//CloudWatch-32.png)
![CloudWatch](/images/4//CloudWatch-33.png)
![CloudWatch](/images/4//CloudWatch-34.png)
![CloudWatch](/images/4//CloudWatch-35.png)
![CloudWatch](/images/4//CloudWatch-36.png)
3. Create Cloud Alarm for event **RestoreObject**
![CloudWatch](/images/4//CloudWatch-37.png)
![CloudWatch](/images/4//CloudWatch-38.png)
![CloudWatch](/images/4//CloudWatch-39.png)
![CloudWatch](/images/4//CloudWatch-40.png)
![CloudWatch](/images/4//CloudWatch-41.png)
![CloudWatch](/images/4//CloudWatch-42.png)
![CloudWatch](/images/4//CloudWatch-43.png)
