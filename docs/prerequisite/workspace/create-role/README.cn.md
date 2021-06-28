---
title: 创建 IAM 角色
weight: 2
---

1. 打开 [链接](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2&policies=arn:aws:iam::aws:policy%2FAdministratorAccess) 来创建一个拥有管理员权限的 IAM 角色 
2. 确认选择了**AWS服务**和**EC2**，然后点击**Next: Permissions**查看权限。 

![IAM Role EC2](/images/iam-role-ec2.png)

3. 确认**AdministratorAccess**被勾选，然后点击**Next**。

![IAM Role Admin Permission](/images/iam-role-administratorAccess.png)

4. 名称输入`gcr-rs-dev-workshop-admin`，点击**Create Role** 

![IAM Role Created](/images/iam-role-name-create.png)


