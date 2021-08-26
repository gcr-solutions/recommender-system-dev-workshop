---
title: 创建 IAM 角色
weight: 2
---

1. 您需要为 Cloud9 服务创建 IAM 权限, 该权限遵守最小权限设置原则，包含了以下 AWS 服务：
   - AWS IAM
   - AMAZON S3
   - AMAZON EKS
   - AWS SecretsManager
   - AWS CodeBuild
   - AWS EFS
   - AWS EC2
   - AWS Elasticache
   - AWS CloudWatch
   - AWS AutoScaling
   - AWS SSM
   - AWS KMS
   - AWS AutoScaling
   - AWS CloudFormation
   
2. 首先打开 [策略链接](https://github.com/gcr-solutions/recommender-system-dev-workshop-code/blob/main/scripts/role/gcr-rs-role.json), 复制 gcr-rs-role.json 文件中的内容。

3. 打开创建策略的 [链接](https://console.aws.amazon.com/iam/home#/policies$new?step=edit), 在 JSON 栏中粘贴上一步复制的内容，**注意**: 请将 `<account_id>` 改为您的AWS 账户 ID。完成后点击下一步。

   ![CREATE POLICY](/images/create-iam-policy.png)
   
4. 在策略名字上输入 `gcr-rs-dev-workshop-admin-policy`， 点击**创建策略**。
   
5. 点击创建 IAM 角色的[链接](https://console.aws.amazon.com/iam/home#/roles$new?step=review&commonUseCase=EC2%2BEC2&selectedUseCase=EC2), 确认选择了**AWS服务**和**EC2**，然后点击下一步查看权限。

   ![IAM Role EC2](/images/iam-role-ec2.png)

6. 搜索刚刚创建的策略 `gcr-rs-dev-workshop-admin-policy` 并勾选，然后点击下一步。

   ![IAM Role Least Permission](/images/iam-role-leastPermission.png)

7. 名称输入`gcr-rs-dev-workshop-admin`，点击**创建角色**。

   ![IAM Role Created](/images/iam-role-name-create.png)


