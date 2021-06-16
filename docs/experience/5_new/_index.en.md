---
title: New Items Added And Batch Update
weight: 45
---

The recommender system does not only have new action data collected. In real scenario, new items, e.g. news, movies, music..., will be added to the system and should be integrated in the whole system. We have prepared the logic for adding news items. Suppose We have some news to be added:

![news-to-add](/images/news-to-add.png)


Add new items to recommender system
```shell
cd /home/ec2-user/environment/recommender-system-solution/sample-data

./new_item_to_s3.sh

```

You should never see them before. First, you should run the offline logic for new content:

![item-offline](/images/item-offline.png)

The logic behind this function is shown below:

![content-logic-image](/images/content-logic-image.png)

You can tell that the whole news are analyzed at first and then relating models are updated.

{{% notice info %}}
This will take about 30 minutes to finish
{{% /notice %}}

When all these functions are finished, you should likely see these added news recommended for you in the system:

![new-recommend](/images/new-recommend.png)

In regular maintenance, you can trigger batch process offline function to generate the recommendation list for each user. These results will be loaded in the redis and can be fetched on line.








