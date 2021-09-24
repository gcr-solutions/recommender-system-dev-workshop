---
title: 清理资源
weight: 60
---

希望您喜欢该动手实验并学到了新的知识。 为了避免产生不必要的收费，请按照以下步骤来清理所有的资源： 

1. 在终端命令行中，运行以下命令删除推荐系统的在线部分： 
    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./clean-online.sh >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log
    ```
   
   {{% notice info %}}
   这将需要大约 20 分钟来释放资源 
   {{% /notice %}}

2. 运行以下命令删除推荐系统的离线部分： 
    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./clean-offline.sh >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log
    ```
   
   {{% notice info %}}
   当您执行完以上步骤，推荐系统的在线与离线部分已经删除完成。若您想彻底清空所有资源，您还需执行以下步骤：
   {{% /notice %}}

3. 打开 [IAM Role 控制台](https://console.aws.amazon.com/iam/home#/roles), 选择并删除开头为 `gcr-rs-dev-workshop-ec2` 的 IAM 角色。

   ![GCR RS DEV](/images/gcr-rs-dev.png)

4. 打开 [Cloudformation 控制台](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/), 选择并删除以下项目：

   - `gcr-rs-dev-workshop-ec2` 
   - `rs-dev-workshop-codebuild-role-stack`
   
5. 在 [EC2 Key Pairs](https://console.aws.amazon.com/ec2/v2/home#KeyPairs:search=gcr-rs-dev-workshop-key) 中, 选择并删除 `gcr-rs-dev-workshop-key`。

6. 删除您保存的 `gcr-rs-dev-workshop-ec2-key.pem` 文件。假如您使用的是 Macbook，请执行以下命令：

   ```sh
   cd ~/Downloads
   rm -f gcr-rs-dev-workshop-ec2-key.pem
   ```

