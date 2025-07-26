---
title : "Create the Source S3 Bucket"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---


#### Create the Source S3 Bucket
Create a bucket in Amazon S3 to store the input data, which is where the automation process of storing data to Glacier begins.
1. Go to the [Amazon Web Service homepage](https://aws.amazon.com/) page.
2. Select **S3** service
![Select S3 Service](S3-Select.PNG)
1. Select **S3**, click ***Create Bucket***.
![Select S3 Create Bucket](S3-Select-Create-Bucket.PNG)
1. Enter information for the bucket to be created:
- Bucket name: `archival-source-bucket-<yourID>` to avoid confusion
- Object Ownership: leave as **default** (Bucket owner enforce)
- Block Public Access: keep **default** (**ALL enabled**)
![Create Bucket](Create-Bucket-1.png)
- Enable **Versioning**: Tick “**Enable**”
- Enable **Object Lock**: Tick “**Enable**”
- Tick: "**I acknowledge that enabling Object Lock will permanently allow objects in this bucket to be locked.**"


![Create Bucket](Create-Bucket-2.png)
![Create Bucket](Create-Bucket-3.png)
- Select **Create Bucket**
- ![Create Bucket](Create-Bucket-4.png)
- Try adding an object to the bucket and setting a legal hold for that object
![Add Object](Add-Object-1.png)
![Add Object](Add-Object-2.png)
![Add Object](Add-Object-3.png)
![Add Object](Add-Object-4.png)
- **Legal hold**: 
  - Keep data for legal reasons (legal case, investigation).
  - No expiration date – keep indefinitely until discarded.
  - Can manually turn on/off each object.
- **Retention Policy**: 
  - Keep data for a certain period of time.
  - Has a specific term (e.g. 7 years).
  - Cannot be deleted or overwritten until expired.
![Add Object](Add-Object-5.png)
![Add Object](Add-Object-6.png)
![Add Object](Add-Object-7.png)
![Add Object](Add-Object-8.png)