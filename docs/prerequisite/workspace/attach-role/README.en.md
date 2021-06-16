---
title: Attach the IAM role to your workspace
weight: 3
---

1. In the Cloud9 workspace, click the grey circle button (in top right corner) and select **Manage EC2 Instance**.

![Cloud9 Manage EC2 Instance](/images/cloud9-manage-ec2.png)

2. EC2 dashboard will be opened, select the "aws-cloud9-gcr-rs-workshop-xxx" instance, then choose **Actions / Security / Modify IAM Role**

![EC2 Modify Role](/images/ec2-modify-role.png)

3. Choose **gcr-rs-workshop-admin** from the **IAM Role** drop down, and select **Save**

![EC2 Modify Role](/images/ec2-select-role.png)

