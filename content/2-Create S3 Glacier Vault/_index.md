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
![S3 Glacier](/images/2/Select-S3-Glacier.png)
2. Select ***Create vault***
![S3 Glacier](/images/2/Create-Vault.png)
3. Configuration:
- Vault name: `compliance-archive-vault`
- Event notifications: Default is **Turn off notifications**
![S3 Glacier](/images/2/Create-Vault-1.png)

#### Deploy Vault Lock Policy (very important)
1. In the Vault list, select `compliance-archive-vault`.
![Create Vault Policy](/images/2/Vault-Policy.png)
1. Switch to the **Vault policies** tab.
![Create Vault Policy](/images/2/Vault-Policy-1.png)
1. Click **Initiate Vault Lock**.
2. Create a Vault Lock policy as follows:
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

1. Copy the Lock ID on the screen, then select Close
![Create Vault Policy](/images/2/Vault-Policy-2.png)


1. Click **Complete Vault Lock policy**, tick on "**I acknowledge that completing the Vault Lock is irreversible.**", enter the copied **Lock ID**, select **Complete Vault Lock**.
![Create Vault Policy](/images/2/Vault-Policy-3.png)
![Create Vault Policy](/images/2/Vault-Policy-4.png)
![Create Vault Policy](/images/2/Vault-Policy-5.png)