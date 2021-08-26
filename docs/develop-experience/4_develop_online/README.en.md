---
title: Develop Online Of Recommender System
weight: 44
---

In this part, you'll change some code to add two features in online part, and then deploy them to your Recommender System.

1. Add hot topic
- Open `recommender-system-dev-workshop-code/src/filter/plugins/news/service.py` file
- Go to line 355 and uncomment below code.
    ```
    # hot_topic_news_list = self.get_hot_topic_news_list(user_id, hot_topic_count, present_recommend_news_id_list, recommended_news_list)
    ```
- Push your change to your github repo

    ```
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/src/filter/plugins/news
    git pull
    git add service.py
    git commit -m "test for online development"
    git push
    ```

- Go to [codebuild project](https://console.aws.amazon.com/codesuite/codebuild/projects) to check **gcr-rs-dev-workshop-filter-build**, it should be triggered.
- After **gcr-rs-dev-workshop-filter-build** succeeded, ArgoCD will deploy filter services in 3 minutes, please go to ArgoCD to check it.
- Verify it.
After clicking at three pieces of news, you will see the recommendation list in the first channel. The recommendation result consists of two parts. The first 
part is top recommendation according to the most interested type in your portrait. In this example, it seems that **gcr-rs-admin** is very interested in
the entertainment, the first 2-3 lines of recommendation list are entertainment news:
![Top-Type-News](/images/top-type-news.png)

2. Add portrait recall. The recommender system that you just deployed only has recall according to user recent clicked, and you'll follow below steps to add another recall according to user portrait.
- Open `/recommender-system-dev-workshop-code/src/recall/plugins/news/service_impl.py` file
- Go to line 142 and uncomment below code.
    ```
    # self.recall_by_portrait(user_portrait, recall_wrap, recall_items, multiple_shot_record)
    ```
- Push your change to your github repo

    ```
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/src/recall/plugins/news
    git pull
    git add service_impl.py
    git commit -m "test for online portrait"
    git push
    ```

- Go to [codebuild project](https://console.aws.amazon.com/codesuite/codebuild/projects) to check **gcr-rs-dev-workshop-recall-build**, it should be triggered.
- After **gcr-rs-dev-workshop-recall-build** succeeded, ArgoCD will deploy filter services in 3 minutes, please go to ArgoCD to check it.
- Verify it. After clicking at three pieces of news, recall process will be triggered, you can go to argo cd server to check recall service log, you should see **portrait_** text in **recall result**

    ![check-recall-service](/images/check-recall-service.png)

    ![recall-log](/images/recall-log.png)

