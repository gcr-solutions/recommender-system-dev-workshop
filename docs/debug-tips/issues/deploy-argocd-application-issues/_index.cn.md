---
title: 创建 Argo CD 应用
weight: 72
---

1. 如果在您执行此步骤时出现以下错误：
    ```
    An error occurred (ResourceNotFoundException) when calling the UpdataFunctionConfiguration operation: Function not found: ... :rs-dev-workshop-SNSMessageLambda
    ```
   则证明您的Lambda未创建成功。 检查您的 Lambda 服务是否拥有 `S3: CreateBucket` 权限， 若没有， 您需要先创建一个 S3 桶，桶名为 `aws-gcr-rs-sol-dev-workshop-${REGION}-${AWS_ACCOUNT_ID}` 。

2. 如果在您执行此步骤时，部分 pod 的心跳长时间显示失败，如下所示：
   
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
