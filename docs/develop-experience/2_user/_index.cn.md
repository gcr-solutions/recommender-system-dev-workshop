---
title: 浏览推荐系统
weight: 42
---

## 探索用户体验
将刚才生成的网址复制到浏览器中，会看到如下页面： 

![End-User-GUI](/images/end-user-gui.png)

您可以在表格中输入您的用户名： 

![Name-Input-Field](/images/name-input-field.png)

然后点击登录按钮：

![Login-Icon](/images/login-icon.png)

下次，您可以输入相同的用户名用来根据相关历史记录获得推荐。 或者，您可以点击随便看看按钮，该方式登录时每次都会将您视为新用户： 

![Look-Around](/images/look-around.png)

如果您以 `gcr-rs-admin` 的管理员身份登录系统。 您将看到以下页面： 

![Cold-Start](/images/cold-start.png)

您可以在右上角查看您的访问次数： 

![Login-Time](/images/login-time.png)

您应该看到阅读历史和用户画像都是空的： 

![Empty-History-Portrait](/images/empty-history-portrait.png)

因为您是新用户，所以推荐系统会以**冷启动逻辑**为您生成推荐列表。 在冷启动逻辑中，随机抽取不同类型的新闻： 

![Cold-Start-News](/images/cold-start-news.png)

您可以浏览不同类型的新闻并点击您喜欢的内容。 您可以观察到阅读历史和用户画像会发生相应的变化： 

![Different-Types-News](/images/dtn.png)

第二部分是根据您浏览过的内容的关键词进行推荐的。 如果再次点击“推荐”，您将获得另一个推荐列表： 

![Recommend-type-1](/images/recommend-type-1.png)

您还会注意到，在用户画像中您喜欢的类别有兴趣度值： 

![User-Portrait](/images/user-portrait.png)

如果您浏览推荐列表，您会注意到一些带有多样性的标签。 这意味着系统将推送您从未阅读过的某些类型的新闻用来发现您可能感兴趣的类型： 

![Disparity](/images/disparity.png)

现在，您了解了这个演示的所有内容。 请随意点击尝试！ 

## 如何生成推荐列表（可选） 

如果您有兴趣进一步了解该系统背后的逻辑，可以查看以下内容。 

如果是第一次登录，推荐列表会来自冷启动逻辑。 并且每次点击新闻，用户画像都会更新。 

如果您点击新闻至少 3 次，推荐列表将来自一个逻辑序列，从召回到过滤： 

![Application Logic](/images/application-logic.png)

在真实的推荐系统中，将复杂的模型应用于训练所有物品并不是一个好主意。 我们需要一些有效的方法来为当前用户找到更有可能被推荐的物品，这就是召回（检索）阶段应该做的事情。 例如，召回逻辑可以从全部 1,000,000 项中找到前 1,000 项。 然后，我们使用复杂的算法对这 1,000 个项目进行排名并找到前 100 个项目。 在推送给最终用户之前，我们可能会为这些排名项目添加一些自定义逻辑，例如视差逻辑，这个阶段称为过滤逻辑： 

![Recall-Rank-Filter](/images/recall-rank-filter.png)

这是4路召回逻辑，包括新闻类型、新闻关键词、从知识图谱学习的新闻实体嵌入和用户画像。 召回逻辑从这些角度找到最有希望的候选者： 

![Recall-Logic](/images/recall-logic.png)

排名逻辑是通过基于知识图谱的排名算法（DKN）实现的。 当前用户的点击记录被发送到训练模型，所有新闻都通过知识图谱进行编码，然后模型将预测当前用户是否会点击这些新闻： 

![Rank-Logic](/images/rank-logic.png)






