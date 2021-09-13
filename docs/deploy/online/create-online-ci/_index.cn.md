---
title: 创建在线 CodeBuild 项目
weight: 1
---

在此步骤中，您将创建 AWS CodeBuild 项目来构建推荐系统**在线部分**的服务，包括 **demo**、**event**、**filter**、**loader**、**portrait**、**rank**、**recall**、**retrieve**、**ui**。

1. 运行以下命令创建在线CodeBuild项目

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh online-codebuild > ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```
   
{{% notice info %}}
这将需要大约 10 分钟进行配置
{{% /notice %}}

2. 进入[AWS Codebuild 控制台](https://console.aws.amazon.com/codesuite/codebuild/home) 查看并确保所有的项目已经创建成功。**注意**：如果有项目构建失败，请重新构建该项目。
    
    ![Codebuild Succeed](/images/codebuild-successfully.png)
