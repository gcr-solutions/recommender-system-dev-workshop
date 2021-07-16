---
title: 问题解答
weight: 70
---

在您部署期间，如果您遇到了以下问题，请查看相关解决方式：

1. 如果在您执行 **创建 Argo CD 应用** 时出现以下错误：
```
   An error occurred (ResourceNotFoundException) when calling the UpdataFunctionConfiguration operation: Function not found: ... :rs-dev-workshop-SNSMessageLambda
```
   则证明您的Lambda未创建成功。 检查您的 Lambda 服务是否拥有 `S3: CreateBucket` 权限， 若没有， 您需要先创建一个 S3 桶，桶名为 `aws-gcr-rs-sol-dev-workshop-${REGION}-${AWS_ACCOUNT_ID}` 。

2. 如果在您执行 **创建 Argo CD 应用** 时，部分 pod 的心跳长时间显示失败，如下所示：
   
![argocd heart unhealthy](/images/argocd-heart-unhealthy.png)

可能因为您的 redis 配置信息设置失败。 打开您的 Cloud9 控制界面，在左侧文件栏中点击 `/manifest/envs/news-dev/config.yaml` 文件，文件内容应该如下所示：

![fix redis bug](/images/redis-bug.png)

如果您的 redis_port 或者 redis_host 为空，请打开 [链接](https://console.aws.amazon.com/elasticache/home), 在左侧栏选择 Redis，选中 `gcr-rs-dev-workshop-redis-cluster`：

![redis console](/images/redis-console.png)

将 Primary Endpoint 的内容按照 redis_host:redis_port 的格式复制到 config.yaml 文件中, 并输入以下命令更新配置：

```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/
git pull
git add ./manifests/envs/news-dev/config.yaml
git commit -m "update config"
git push
```

3. 如果登陆推荐系统演示网站后，出现 500 的错误， 请打开 Argo CD 网站，确保所有 Pod 创建成功。若有 Pod 失败，请查看该 Pod 的 log 信息， 如下所示：

![pod failed log](/images/pod-failed-log.png)

若显示地区不对，请参考问题二的方式修改 config.yaml 文件中的地区。 若显示没有权限，请跳转到**创建 IAM 角色**步骤增加相应的权限。
