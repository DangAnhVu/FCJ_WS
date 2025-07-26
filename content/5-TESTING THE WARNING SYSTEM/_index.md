---
title : "Testing The Waning System"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

1. Test DeleteObject warning
- First you open the created bucket to save data.
![Testing The Waning Sytem](/images/5/1.png)
- We upload any file to that bucket.
![Testing The Waning Sytem](/images/5/2.png)
![Testing The Waning Sytem](/images/5/3.png)
![Testing The Waning Sytem](/images/5/4.png)
- Then enable versioning of the object, select the newly added object, select delete.
![Testing The Waning Sytem](/images/5/5.png)
![Testing The Waning Sytem](/images/5/6.png)
![Testing The Waning Sytem](/images/5/7.png)
- See alarm DeleteBucket on CloudTrail and CloudWatch console
![Testing The Waning Sytem](/images/5/17.png)
- Email alarm
![Testing The Waning Sytem](/images/5/9.png)

1. Test DeleteBucket warning
- First you create bucket with name `test-delete-< Your-ID >`
- ![Testing The Waning Sytem](/images/5/10.png)
- ![Testing The Waning Sytem](/images/5/11.png)
- You delete that bucket
![Testing The Waning Sytem](/images/5/12.png)
![Testing The Waning Sytem](/images/5/13.png)
- See alarm DeleteBucket on CloudTrail and CloudWatch console
![Testing The Waning Sytem](/images/5/14.png)
![Testing The Waning Sytem](/images/5/15.png)
![Testing The Waning Sytem](/images/5/16.png)