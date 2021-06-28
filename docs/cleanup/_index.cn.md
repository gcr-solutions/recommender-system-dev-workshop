---
title: 清理资源
weight: 60
---

希望您喜欢该 workshop 并学到了新的知识。 为了避免产生不必要的收费，请按照以下步骤来清理所有的资源： 

1. 在 Cloud9 终端命令行中，运行以下命令删除推荐系统的在线部分： 
```sh
cd /home/ec2-user/environment/recommender-system-solution/scripts
./clean-online.sh
```

{{% notice info %}}
这将需要大约 20 分钟来释放资源 
{{% /notice %}}

2. 在 Cloud9 终端命令行中，运行以下命令删除推荐系统的离线部分： 
``` 

cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./clean-offline.sh

```

3.在 [Cloud9 控制台](https://ap-northeast-1.console.aws.amazon.com/cloud9/home?region=ap-northeast-1#) 中，选择并删除 `gcr-rs-workshop env `。

4. 在 [IAM 角色控制台](https://console.aws.amazon.com/iam/home#/roles) 中, 选择并删除 `gcr-rs-dev-workshop-admin` 角色。

5. 在 [EC2 Key Pairs](https://ap-northeast-1.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-1#KeyPairs:search=gcr-rs-dev-workshop-key) 中, 选择并删除 `gcr-rs-dev-workshop-key`。

6. 打开您的 Github 账户，删除您 fork 的推荐系统仓库。

