---
title: Develop Online of Recommender System
weight: 44
---

In this part, you'll change some code to add two features in online part, and then deploy them to your Recommender System.

1. Add hot topic
- Open `recommender-system-dev-workshop-code/src/filter/plugins/news/service.py` file
- Change code, because we already prepared the code, you just need to uncomment below code.
``
# hot_topic_news_list = self.get_hot_topic_news_list(user_id, hot_topic_count, present_recommend_news_id_list, recommended_news_list)
``
- Push your change to your github repo
- Go to [codebuild project](https://ap-northeast-1.console.aws.amazon.com/codesuite/codebuild/projects?region=ap-northeast-1) to check **gcr-rs-dev-workshop-filter-build**, it should be triggered.
- After **gcr-rs-dev-workshop-filter-build** succeeded, go to ArgoCD server to check, filter should be deployed again.
- Verify it.

After clicking at three pieces of news, you will see the recommendation list in the first channel. The recommendation result consists of two parts. The first 
part is top recommendation according to the most interested type in your portrait. In this example, it seems that **gcr-rs-admin** is very interested in
the entertainment, the first 2-3 lines of recommendation list are entertainment news:
![Top-Type-News](/images/top-type-news.png)
TODO @Aoyu

2. Add portrait recall. The recommender system that you just deployed only has recall according to user recent clicked, and you'll follow below steps to add another recall according to user portrait.
- Open `/recommender-system-dev-workshop-code/src/recall/plugins/news/service_impl.py` file
- Change code, because we already prepared the code, you just need to uncomment below code.
``
# self.recall_by_portrait(user_portrait, recall_wrap, recall_items, multiple_shot_record)
``
- Push your change to your github repo
- Go to [codebuild project](https://ap-northeast-1.console.aws.amazon.com/codesuite/codebuild/projects?region=ap-northeast-1) to check **gcr-rs-dev-workshop-recall-build**, it should be triggered.
- After **gcr-rs-dev-workshop-recall-build** succeeded, go to ArgoCD server to check, filter should be deployed again.
- Verify it.
TODO Aoyu
