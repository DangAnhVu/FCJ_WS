---
title : "Clean Up Resources"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

1. Delete trail created in **Cloudtrail**.
![Delete Trail](1.png)
2. Empty and delete bucket log in S3.
![Delete Bucket log](2.png)
![Delete Bucket log](3.png)
![Delete Bucket log](4.png)
![Delete Bucket log](5.png)
3. Delete related topics and subcriptions on SNS.
- Delete Topic: 
![Delete Topic](6.png)
![Delete Topic](7.png)
  - Do the same with **Delete Bucket**
  - Do the same with **Delete Object**
- Delete Subscription: 
![Delete Topic](8.png)
![Delete Topic](9.png)
- Do the same with the rest.
4. Delete alarms created in CloudWatch.
![Delete alarm](10.png)
![Delete alarm](11.png)
5. Empty and delete bucket used for automatic storage in S3.
- Empty bucket: 
![Delete Bucket](12.png)
![Delete Bucket](13.png)
{{% notice info %}}
Remember to turn off legal holds on objects and turn on object versioning to delete without errors.
{{% /notice %}}
- Delete Bucket:
![Delete Bucket](14.png)
![Delete Bucket](15.png)