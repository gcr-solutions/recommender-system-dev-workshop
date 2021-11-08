---
title: Environment
weight: 10
---

## AWS Account
In order to complete this workshop you’ll need an AWS Account, and an AWS IAM user in that account with at least IAMFullAccess permission, and the permissions included in the [link](https://github.com/gcr-solutions/recommender-system-dev-workshop-code/blob/main/scripts/role/gcr-rs-user-role.json). If you don’t have, create one now by clicking [here](https://aws.amazon.com/getting-started/)

**Cost**: Some, but NOT all, of the resources you will launch as part of this workshop are eligible for the AWS free tier if your account is less than 12 months old. See the [AWS Free Tier page](https://aws.amazon.com/free/) for more details. To avoid charges for endpoints and other resources you might not need after you’ve finished a workshop, please refer to the [Cleanup Module](../../cleanup/)

## AWS Region
This workshop is shown in **(Tokyo)ap-northeast-1** and **(Beijing)cn-north-1**. **Attention**: If you want to deploy Amazon Personalize recommended method, please select the following region:

- us-east-1 (N.Virginia)
- us-east-2 (Ohio)
- us-west-2 (Oregon)
- ap-south-1 (Mumbai)
- ap-northeast-2 (Seoul)
- ap-southeast-1 (Singapore)
- ap-southeast-2 (Sydney)
- ap-northeast-1 (Tokyo)
- ca-central-1 (Central)
- eu-central-1 (Frankfurt)
- eu-west-1 (Ireland)

## Browser
We recommend you use the latest version of **Chrome** to complete this workshop.

## SageMaker Resource Requirement
To test certain workshop functions, your SageMaker resource limit need to meet the minimum requirement as below. 

[comment]: <> (Check and increase the SageMaker resource limit by clicking https://sagemaker-tools.corp.amazon.com/limits )

|Resource type |Resource | 	Required limit |
|--- | --- | --- |
|SageMaker Training |training-job/ml.p2.xlarge |2|
|SageMaker Processing |processing-job/ml.m5.large |2|
|VPC| - | 2 |

