---
title: 清理资源
weight: 60
---

希望您喜欢该动手实验并学到了新的知识。 为了避免产生不必要的收费，请按照以下步骤来清理所有的资源： 

1. 在 Cloud9 终端命令行中，运行以下命令删除推荐系统的在线部分： 
    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./clean-online.sh
    ```
   
   {{% notice info %}}
   这将需要大约 20 分钟来释放资源 
   {{% /notice %}}

2. 在 Cloud9 终端命令行中，运行以下命令删除推荐系统的离线部分： 
    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./clean-offline.sh
    ```

3. 打开您的 Github 账户，在您复刻的推荐系统仓库中点击**设置**，找到**Webhooks**栏并删除所有资源。
   
**注意**： 当您执行完以上步骤，推荐系统的在线与离线部分已经删除完成。若您想彻底清空所有资源，您还需执行以下步骤：

4. 在 [Cloud9 控制台](https://console.aws.amazon.com/cloud9/home) 中，选择并删除 `gcr-rs-workshop env `。

5. 在 [IAM 角色控制台](https://console.aws.amazon.com/iam/home#/roles) 中, 选择并删除 `gcr-rs-dev-workshop-admin` 角色。

6. 在 [EC2 Key Pairs](https://console.aws.amazon.com/ec2/v2/home#KeyPairs:search=gcr-rs-dev-workshop-key) 中, 选择并删除 `gcr-rs-dev-workshop-key`。

7. 打开您的 Github 账户，删除您复刻的推荐系统仓库。

