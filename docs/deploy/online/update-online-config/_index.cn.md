---
title: 更新在线部分配置
weight: 4
---

在此步骤中，您将根据先前创建的基础设施来更新在线服务配置。

1. 运行以下命令更新本地配置，包括：
    - Elasticache(Redis) endpoint
    - AccountId
    - Region

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh config
    ```

3. 通过以下命令将更新过的文件推送到您的 CodeCommit 仓库：

    ```sh
    git pull
    git add -A
    git commit -m "update config"
    git push
    ```