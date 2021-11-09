---
title: 部署离线部分
weight: 1
---

1. 选择您想要部署的推荐场景与推荐方式。 首先输入以下命令，修改 `setup-rs-system.sh` 脚本中的环境变量：

   ```shell
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   vim setup-rs-system.sh
   ```

   将 SCENARIO 变量的值设置为您想要部署的推荐场景，可设置为 `news` 或 `movie`。将 METHOD 变量的值设置为您想要部署的推荐方式，可设置为 `customize`、`ps-complete` 、 `ps-rank` 、 `ps-sims` 。保存修改后的脚本。

2. 运行以下命令部署离线部分

    ```sh 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh deploy-offline >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

3. 进入 [AWS codebuild 控制台](https://console.aws.amazon.com/codesuite/codebuild/projects) ，检查你的代码构建项目，搜索`rs-dev-workshop-offline-`，确保所有的项目构建成功。

   {{% notice info %}}
   这将需要大约 20 分钟的时间进行配置
   {{% /notice %}}

   ![Offline CodeBuild Success](/images/offline-codebuild-success.png)






