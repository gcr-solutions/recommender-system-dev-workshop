---
title: 切换推荐方式
weight: 48
---

Amazon Personalize是一项完全托管的个性化推荐服务，包含了多种算法。这些算法基于Amazon零售业务二十多年的个性化经验与开发专业知识。GCR 个性化推荐系统提供了三种集成Amazon Personalize的方案，您可以一键式切换至不同的方案，对比它们的推荐结果，并选择出最适合您当前业务的推荐系统方案。三种方案如下表所示：

|方案 |使用的Amazon Personalize配方 | 方案介绍 | 代号 |
|--- |--- | --- | --- |
|完整替代方案|aws-user-personalization |如果您只想使用Amazon Personalize服务来实现用户的个性化推荐，那么可以采用此方案。此方案的在线部分提供了Amazon Personalize服务的实际用例，离线部分提供了模型更新、新物品上线、添加新用户三种功能的自动化流程。此方案能够极大的加快您上手与部署Amazon Personalize服务的时间。 |ps-complete|
|排序模型替代方案|aws-personalized-ranking |GCR 个性化推荐系统现有的排序模型是基于知识图谱的DKN模型。 如果您想使用Amazon Personalize提供的排序模型，可以采用此方案。此方案的在线部分将排序模块的 DKN 模型替换成 aws-personalized-ranking 模型。离线部分在原有流程的基础上，增加了Amazon Personalize服务的模型训练与数据集导入流程，并在排序模块的批量更新（rank batch）中将模型替换成了 aws-personalized-ranking 模型。 |ps-rank|
|添加召回逻辑方案|aws-sims |GCR 个性化推荐系统现有的召回模型包含了四路召回逻辑。 如果您想使用Amazon Personalize提供的物品相似度模型作为第五路召回逻辑的话，可以采用此方案。此方案的在线部分在召回模块中多增加了一路召回逻辑，该召回逻辑采用了 aws-sims 物品相似度配方。离线部分在原有流程的基础上，增加了Amazon Personalize服务的模型训练与数据集导入流程，并在召回模块的批量更新（recall batch）中增加了 aws-sims 实现的一路召回逻辑。 |ps-sims|


若您想切换至**完整替代方案**，执行以下命令：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./setup-rs-system.sh change-method ps-complete
```

若您没有部署 **ps-complete** 相关资源，您会得到以下提醒，请执行以下命令。

![ps-complete not exist](/images/ps-complete-not-exist.png)

执行完毕后，ArgoCD会在3分钟内部署服务，打开 Argo CD 网页，您会看到容器正在同步更新。若没有显示，请点击 **REFRESH** 。部署过程大概需要 1 分钟。

![Argo CD Sync](/images/argocd-sync-method.png)

等待同步完成后，打开新闻界面，此时推荐系统已改为完全从Amazon Personalize服务中获取结果。点击**推荐**按钮，打开Argo CD网站中的 Retrieve Pod，可以在 LOGS 栏的最下面看到获取的推荐列表含有 **ps-complete**，代表推荐列表从 Amazon Personalize 服务中获得。

![ps complete log](/images/ps-complete-result.png)

若您想切换至**排序模型替代方案**，执行以下命令：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./setup-rs-system.sh change-method ps-rank
```

若您没有部署 **ps-rank** 相关资源，您会得到以下提醒，请执行以下命令。

![ps-rank not exist](/images/ps-rank-not-exist.png)

执行完毕后，打开 Argo CD 网页，等待同步完成。

打开新闻界面，此时推荐系统的排序模型已改为 aws-personalized-ranking 模型。点击三篇新闻，打开Argo CD网站中的 Rank Pod，可以在 LOGS 栏的最下面看到由 **ps-rank** 实现的排序功能。

![ps rank log](/images/ps-rank-result.png)

若您想切换至**添加召回逻辑方案**，执行以下命令：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./setup-rs-system.sh change-method ps-sims
```

若您没有部署 **ps-sims** 相关资源，您会得到以下提醒，请执行以下命令。

![ps-sims not exist](/images/ps-sims-not-exist.png)

执行完毕后，打开 Argo CD 网页，等待同步完成。

打开新闻界面，此时推荐系统的召回模型已添加了 aws-sims 实现的一路召回逻辑。点击三篇新闻，打开Argo CD网站中的 Recall Pod，可以在 LOGS 栏的最下面看到由 **ps-sims** 实现的召回逻辑。

![ps sims log](/images/ps-sims-result.png)

若您想返回到用户定制化方法，只需执行以下命令，并刷新Argo CD即可：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./setup-rs-system.sh change-method customize
```


## 如何切换至不同方法（可选） 

如果您有兴趣进一步了解该功能背后的逻辑，可以查看以下内容。 

当您执行完 `./setup-rs-system.sh change-method $METHOD` 后，您可以看到终端输出了以下内容：

![change method output](/images/change-method-output.png)

该脚本执行了以下步骤：

1. 通过传入的 **METHOD** 参数，更新配置文件（ps_config.json）中的 Personalize 方案名与活动名。

2. 通过调用 Amazon Personalize 服务的接口，查询最新的版本号，并更新至配置文件（ps_config.json）。   

3. 将更新完的配置文件同步到 AWS S3 桶中。

4. 通知在线系统的 Loader 服务去从 AWS S3 桶中下载最新的配置文件。

5. 更新 AWS EKS 的 ConfigMap 中的 METHOD 变量值，并将更改提交到 AWS CodeCommit 的仓库中。

当 ConfigMap 更新后，Argo CD 将会在 3 分钟内自动同步服务，流程图如下所示：

![change method process](/images/change-method-process.png)




