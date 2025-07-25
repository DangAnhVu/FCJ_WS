---
title : "Create Glacier Vault and configure Vault Lock Policy"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---
## Objective of this section
- ***Create a Glacier Vault for long-term, low-cost data storage.***
- ***Apply Vault Lock Policy to ensure data is stored in a Write Once Read Many (WORM) model.***
- ***The Vault Lock Policy cannot be modified or deleted after “Lock Complete”, meeting strict compliance controls.***


#### Create Glacier Vault

1. Select ***S3 Glacier***
![S3 Glacier](Select-S3-Glacier.png)
2. Select ***Create vault***
![S3 Glacier](Create-Vault.png)
3. Configuration:
- Vault name: `compliance-archive-vault`
- Event notifications: Default is **Turn off notifications**
![S3 Glacier](Create-Vault-1.png)

#### Deploy Vault Lock Policy (very important)
3. In the Vault list, select `compliance-archive-vault`.
![Create Vault Policy](Vault-Policy.png)
4. Switch to the **Vault policies** tab.
![Create Vault Policy](Vault-Policy-1.png)
5. Click **Initiate Vault Lock**.
6. Create a Vault Lock policy as follows:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PreventDeletion",
      "Effect": "Deny",
      "Principal": "*",
      "Action": [
        "glacier:DeleteArchive",
        "glacier:DeleteVault"
      ],
      "Resource": "<Your Vault ARN>"
    }
  ]
}
```
This policy blocks any archive deletion or vault deletion.

7. Copy the Lock ID on the screen, then select Close
![Create Vault Policy](Vault-Policy-2.png)


8. Click **Complete Vault Lock policy**, tick on "**I acknowledge that completing the Vault Lock is irreversible.**", enter the copied **Lock ID**, select **Complete Vault Lock**.
![Create Vault Policy](Vault-Policy-3.png)
![Create Vault Policy](Vault-Policy-4.png)
![Create Vault Policy](Vault-Policy-5.png)

{{% notice info%}}
Once Complete Vault Lock is confirmed, the policy is immutable.
This ensures regulatory data retention and deletion prevention, essential for compliance audits.
{{% /notice %}}