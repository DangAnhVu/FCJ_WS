---
title : "Set up S3 Lifecycle Policy – Automatically move data from S3 to Glaciers"

weight : 3
chapter : false
pre : " <b> 3. </b> "
---
#### Objective
- Set up a policy to automatically move data from the source S3 Bucket (you created in Step 1) to S3 Glacier for long-term storage.
- Ensure the archival process is automated and consistent, serving compliance.

1. Go to AWS Console → S3 → go to the bucket archival-source-bucket.
![Lifecycle Rule](/images/3/Lifecycle-Rule-1.png)
2. Select the **Management** tab, Select Create lifecycle rule.
![Lifecycle Rule](/public/images/3/Lifecycle-Rule-2.png)

3. Configuration:
- Lifecycle rule name: `Move-to-Glacier-Rule`
- Choose a rule scope: **Apply to all objects in the bucket**
- Apply to all objects in the bucket: Tick on **I acknowledge that this rule will apply to all objects in the bucket.**
- Lifecycle rule actions: Tick **Transition current versions of objects between storage classes**.
![Lifecycle Rule](/images/3/Lifecycle-Rule-3.png)
![Lifecycle Rule](/images/3/Lifecycle-Rule-4.png)

4. Create Rule and Review
![Lifecycle Rule](/images/3/Lifecycle-Rule-5.png)