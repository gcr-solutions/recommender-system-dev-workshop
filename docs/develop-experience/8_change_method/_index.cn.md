---
title: 切换至Amazon Personalize服务 (即将上线)
weight: 48
---

本功能即将上线，您可以将 CloudFormation 模版改成下面链接，来体验内测版本：

```shell
https://aws-gcr-rs-sol-workshop-ap-northeast-1-common.s3.ap-northeast-1.amazonaws.com/rs-dev-workshop-code/github/develop/rs-raw-ec2.yaml
```

Amazon Personalize是一项完全托管的个性化推荐服务，包含了多种算法。这些算法基于Amazon零售业务二十多年的个性化经验与开发专业知识。GCR 个性化推荐系统提供了三种集成Amazon Personalize的方案，您可以一键式切换至不同的方案，对比它们的推荐结果，并选择出最适合您当前业务的推荐系统方案。三种方案如下表所示：

|方案 |使用的Amazon Personalize配方 | 方案介绍 | 代号 |
|--- |--- | --- | --- |
|完整替代方案|aws-user-personalization |如果您只想使用Amazon Personalize服务来实现用户的个性化推荐，那么可以采用此方案。此方案的在线部分提供了Amazon Personalize服务的实际用例，离线部分提供了模型更新、新物品上线、添加新用户三种功能的自动化流程。此方案能够极大的加快您上手与部署Amazon Personalize服务的时间。 |ps-complete|
|排序模型替代方案|aws-personalized-ranking |GCR 个性化推荐系统现有的排序模型是基于知识图谱的DKN模型。 如果您想使用Amazon Personalize提供的排序模型，可以采用此方案。此方案的在线部分将排序模块的 DKN 模型替换成 aws-personalized-ranking 模型。离线部分在原有流程的基础上，增加了Amazon Personalize服务的模型训练与数据集导入流程，并在排序模块的批量更新（rank batch）中将模型替换成了 aws-personalized-ranking 模型。 |ps-rank|
|添加召回逻辑方案|aws-sims |GCR 个性化推荐系统现有的召回模型包含了四路召回逻辑。 如果您想使用Amazon Personalize提供的物品相似度模型作为第五路召回逻辑的话，可以采用此方案。此方案的在线部分在召回模块中多增加了一路召回逻辑，该召回逻辑采用了 aws-sims 物品相似度配方。离线部分在原有流程的基础上，增加了Amazon Personalize服务的模型训练与数据集导入流程，并在召回模块的批量更新（recall batch）中增加了 aws-sims 实现的一路召回逻辑。 |ps-sims|

若您想切换至**完整替代方案**，执行以下命令：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh ps-complete
```

执行完毕后，打开 Argo CD 网页，点击 **REFRESH**，您会看到容器正在同步更新，此过程大概需要 1 分钟。

![Argo CD Sync](/images/argocd-sync-method.png)

等待同步完成后，打开新闻界面，此时推荐系统已改为完全从Amazon Personalize服务中获取结果。点击**推荐**按钮，打开Argo CD网站中的 Retrieve Pod，可以在 LOGS 栏的最下面看到获取的推荐列表含有 **ps-complete**，代表推荐列表从 Amazon Personalize 服务中获得。

![ps complete log](/images/ps-complete-result.png)

若您想切换至**排序模型替代方案**，执行以下命令：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh ps-rank
```

执行完毕后，打开 Argo CD 网页，点击 **REFRESH**，等待同步完成。

打开新闻界面，此时推荐系统的排序模型已改为 aws-personalized-ranking 模型。点击三篇新闻，打开Argo CD网站中的 Rank Pod，可以在 LOGS 栏的最下面看到由 **ps-rank** 实现的排序功能。

![ps rank log](/images/ps-rank-result.png)

若您想切换至**添加召回逻辑方案**，执行以下命令：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh ps-sims
```

执行完毕后，打开 Argo CD 网页，点击 **REFRESH**，等待同步完成

打开新闻界面，此时推荐系统的召回模型已添加了 aws-sims 实现的一路召回逻辑。点击三篇新闻，打开Argo CD网站中的 Recall Pod，可以在 LOGS 栏的最下面看到由 **ps-sims** 实现的召回逻辑。

![ps sims log](/images/ps-sims-result.png)

若您想返回到用户定制化方法，只需执行以下命令，并刷新Argo CD即可：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh customize
```





