---
title: 新物品上线与批量更新
weight: 47
---

推荐系统不仅收集新的行为数据，在实际场景中，新物品例如 新闻、电影、音乐 等将会被添加到系统中并进行重新训练。 我们已经准备好了添加新闻条目的逻辑，假设我们有一些新闻要添加： 

![news-to-add](/images/news-to-add.png)


添加新物品到推荐系统：
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/sample-data

./new_item_to_s3.sh

```

首先，点击**物品上线**运行离线逻辑： 

![item-offline](/images/item-offline.png)

该函数背后的逻辑如下所示：

![content-logic-image](/images/content-logic-image.png)

您可以看到系统将处理与分析所有的数据，并更新相关的模型。

{{% notice info %}}
这将需要大约 30 分钟完成 
{{% /notice %}}

完成新物品上线后，您可以在演示界面的推荐列表中看到这些新增新闻： 

![new-recommend](/images/new-recommend.png)

在定期维护中，您可以点击**批量处理**功能，为所有用户生成推荐列表。 这些结果会被加载到redis中，并可以在线获取。 








