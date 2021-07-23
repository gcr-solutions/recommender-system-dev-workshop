---
title: 开发推荐系统在线部分
weight: 44
---

在这一部分，您将更改一些代码，并在**在线部分**添加两个功能，然后将它们部署到您的推荐系统。

1. 添加热点话题
- 打开`recommender-system-dev-workshop-code/src/filter/plugins/news/service.py`文件
- 转到第 355 行并取消注释下面的代码。
    ```
    # hot_topic_news_list = self.get_hot_topic_news_list(user_id, hot_topic_count, present_recommend_news_id_list, recommended_news_list)
    ```
- 将您的更改推送到您的 github 存储库

    ```
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/src/filter/plugins/news
    git pull
    git add service.py
    git commit -m "test for online development"
    git push
    ```

- 打开 [codebuild 项目](https://console.aws.amazon.com/codesuite/codebuild/projects) 并检查 **gcr-rs-dev-workshop-filter-build**，它应该已经被触发。
- 当**gcr-rs-dev-workshop-filter-build**更新成功后，ArgoCD会在3分钟内部署filter服务，请到ArgoCD查看。
- 验证：当点击三个新闻后，您将看到推荐列表由冷启动逻辑转换成个性化推荐逻辑。 推荐结果由两部分组成，第一部分是根据您的用户画像中最感兴趣的类型进行的顶级推荐。在这个例子中，由于**gcr-rs-admin**对娱乐很感兴趣，所以推荐列表的前3行是娱乐新闻：
  
    ![Top-Type-News](/images/top-type-news.png)

2. 增加用户画像召回功能。 您刚刚部署的推荐系统只是根据用户的最近点击新闻来进行召回，您将按照以下步骤添加根据用户画像进行召回的功能。
- 打开`/recommender-system-dev-workshop-code/src/recall/plugins/news/service_impl.py`文件
- 找到第 142 行并取消注释下面的代码。
    ```
    # self.recall_by_portrait(user_portrait, recall_wrap, recall_items, multiple_shot_record)
    ```
- 将您的更改推送到您的 github 存储库

    ```
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/src/recall/plugins/news
    git pull
    git add service_impl.py
    git commit -m "test for online portrait"
    git push
    ```

- 转到 [codebuild 项目](https://console.aws.amazon.com/codesuite/codebuild/projects) 检查 **gcr-rs-dev-workshop-recall-build**，它应该已经被触发。
- **gcr-rs-dev-workshop-recall-build**成功后，ArgoCD会在3分钟内部署过滤服务，请到ArgoCD查看。
- 验证：点击三个消息后，会触发召回过程，您可以到argo cd服务器查看召回服务日志，您应该在**recall result**中看到 **portrait_** 有关文本。
  
    ![check-recall-service](/images/check-recall-service.png)

    ![recall-log](/images/recall-log.png)

