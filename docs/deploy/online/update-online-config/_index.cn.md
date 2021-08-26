---
title: 更新在线部分配置
weight: 4
---

在此步骤中，您将根据先前创建的基础设施来更新在线服务配置。

1. 跳转到/home/ec2-user/environment/recommender-system-dev-workshop-code/scripts目录

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ```

2. 运行以下命令更新本地配置，包括：
    - Elasticache(Redis) endpoint
    - AccountId
    - Region

    ```sh
    ./setup-rs-system.sh config
    ```

3. 通过以下命令将更新过的文件推送到您的 Github 仓库：

    ```sh
    git pull
    git add ../manifests/envs/news-dev/config.yaml
    git commit -m "update config"
    git push
    ```