---
title: Debug Tips
weight: 70
---

If you encounter the following problems during development, please refer to the related solutions:

1. If you get the following error in the **Create Argo CD Application** step：

```
   An error occurred (ResourceNotFoundException) when calling the UpdataFunctionConfiguration operation: Function not found: ... :rs-dev-workshop-SNSMessageLambda
```

It proves that your Lambda created failed. Check if your Lambda service has `S3: CreateBucket` permission. If not, you need to create an S3 bucket first with the bucket name `aws-gcr-rs-sol-dev-workshop-${REGION}-${AWS_ACCOUNT_ID}`.

2. In the **Create Argo CD Application** step, if the heart status of some pods fails for a long time, as shown below:
   
![argocd heart unhealthy](/images/argocd-heart-unhealthy.png)

It maybe because your redis configuration information setting failed. Open your Cloud9 control interface and click on the file `/manifest/envs/news-dev/config.yaml` on the left file bar. The content of the file should be as follows:

![fix redis bug](/images/redis-bug.png)

If your redis_port or redis_host is empty, please open [link](https://console.aws.amazon.com/elasticache/home), select Redis in the left bar, and select `gcr-rs-dev-workshop-redis-cluster`:

![redis console](/images/redis-console.png)

Copy the content of **Primary Endpoint** to the config.yaml file according to the format of **redis_host:redis_port**, and enter the following command to update the configuration:

```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/
git pull
git add ./manifests/envs/news-dev/config.yaml
git commit -m "update config"
git push
```

3. If a 500 error occurs after logging in to the demo website of the recommendation system, please open the Argo CD website to ensure that all Pods created successfully. If a Pod fails, please check the log information of this Pod, as shown below:

![pod failed log](/images/pod-failed-log.png)

If the displayed region is incorrect, please refer to the second question to modify the region in the **config.yaml** file. If it shows that there is no permission, please go to the **Create IAM Role** step to add the corresponding permission.

