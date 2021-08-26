---
title: 开发推荐系统离线部分
weight: 45
---

## 体验召回逻辑

###  体验不含关键词的召回逻辑

1. 在 argo GUI 中查看召回日志

    ![recall argo log GUI](/images/recall-argo-log.png)

2. 在推荐列表中点击 4 ～ 5 个新闻

    ![recommended list GUI](/images/rs-gui.png)

3. 在 ArgoCD 网站中查看召回服务日志

    ![recall log without keywords](/images/recall-log-nokeywords.png)

###  体验包含关键词的召回逻辑

1. 运行以下脚本来更改召回配置文件：

    ```sh 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./change-recall-config-offline.sh 
    ```

    旧的配置文件：
    
    ![recall config old](/images/recall-config-v1.png)

    新的配置文件：

    ![recall config new](/images/recall-config-v2.png)

    召回配置文件已更改，离线部分通知在线部分加载新的配置文件。点击 [Step Function链接](https://console.aws.amazon.com/states/home#/statemachines) ，搜索 `rs-dev-workshop-News-NotificationStepFunc` 并等待该步骤函数状态为**成功**。
   
   {{% notice info %}}
   此步骤大约需要 4 分钟
   {{% /notice %}}

2. 再次点击推荐列表中的4~5条新闻

    ![recommended list GUI](/images/rs-gui.png)

3. 在 argo GUI 中查看召回日志

    从日志中，我们可以看到更新了新的配置

    ![recall log load new config file](/images/recall-log-loadfile.png)

    可以看到包含关键词的召回日志

    ![recall log with keywords](/images/recall-log-keywords.png)

