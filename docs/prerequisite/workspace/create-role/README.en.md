---
title: Create an IAM role for your workspace
weight: 2
---

1. Follow [this deep link to create an IAM role with Administrator access.](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2&policies=arn:aws:iam::aws:policy%2FAdministratorAccess)
2. Confirm that **AWS service** and **EC2** are selected, then click **Next: Permissions** to view permissions.

![IAM Role EC2](/images/iam-role-ec2.png)

3. Confirm that **AdministratorAccess** is checked, then click **Next** to review.

![IAM Role Admin Permission](/images/iam-role-administratorAccess.png)

4. Enter `gcr-rs-workshop-admin` for the Name, and select **Create Role**

![IAM Role Created](/images/iam-role-name-create.png)


