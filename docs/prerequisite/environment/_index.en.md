---
title: ENVIRONMENT
weight: 10
---

## AWS Account
In order to complete this workshop you’ll need an AWS Account, and an AWS IAM user in that account with at least IAMFullAccess permission, and the permissions included in the [link](https://github.com/gcr-solutions/recommender-system-dev-workshop-code/blob/main/scripts/role/gcr-rs-user-role.json). If you don’t have, create one now by clicking [here](https://aws.amazon.com/getting-started/)

**Cost**: Some, but NOT all, of the resources you will launch as part of this workshop are eligible for the AWS free tier if your account is less than 12 months old. See the [AWS Free Tier page](https://aws.amazon.com/free/) for more details. To avoid charges for endpoints and other resources you might not need after you’ve finished a workshop, please refer to the [Cleanup Module](../../cleanup/)

## Github account
In order to complete this workshop, you also need a github account, if you don't have github account, please follow [signing-up-for-github](https://docs.github.com/en/github/getting-started-with-github/signing-up-for-github) to create github account.

## AWS Region
Once you’ve chosen a region, you should create all of the resources for this workshop there. Accordingly, we recommend running this workshop in **Tokyo** AWS Regions. Use the region drop list to select **Asia Pacific (Tokyo)ap-northeast-1**.

## Browser
We recommend you use the latest version of **Chrome** to complete this workshop.

## SageMaker Resource Requirement
To test certain workshop functions, your SageMaker resource limit need to meet the minimum requirement as below. Check and increase the SageMaker resource limit by clicking [here](https://sagemaker-tools.corp.amazon.com/limits)

|Region |Resource type |Resource | 	Required limit |
|--- |--- | --- | --- |
|ap-northeast-1|SageMaker Training |training-job/ml.p2.xlarge |2|
|ap-northeast-1|SageMaker Processing |processing-job/ml.m5.large |2|

