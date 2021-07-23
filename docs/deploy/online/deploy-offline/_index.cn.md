---
title: 部署离线部分
weight: 2
---

1. 运行以下命令部署离线部分

    ``` 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh deploy-offline
    ```

2. 进入 [AWS codebuild 控制台](https://console.aws.amazon.com/codesuite/codebuild/projects) ，检查你的代码构建项目，搜索`rs-dev-workshop-offline-`，确保下面所有的项目构建成功。

    - `rs-dev-workshop-offline-lambda-build`
    - `rs-dev-workshop-offline-news-step-funcs-build`
    - `rs-dev-workshop-offline-news-inverted-list-build`

    ![Verify offline codebuild](/images/offline-code-build.png)

{{% notice info %}}
这将需要大约 5 分钟的时间进行配置
{{% /notice %}}







