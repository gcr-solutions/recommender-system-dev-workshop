---
title: 部署离线部分
weight: 2
---

1. 运行以下命令部署离线部分

    ```sh 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh deploy-offline >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

2. 进入 [AWS codebuild 控制台](https://console.aws.amazon.com/codesuite/codebuild/projects) ，检查你的代码构建项目，搜索`rs-dev-workshop-offline-`，确保所有的项目构建成功。

   {{% notice info %}}
   这将需要大约 20 分钟的时间进行配置
   {{% /notice %}}

   ![Offline CodeBuild Success](/images/offline-codebuild-success.png)






