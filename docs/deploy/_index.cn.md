---
title: 部署
weight: 30
---

在本模块中，我们将部署 **GCR 推荐系统** 

您需要执行以下步骤：

- [部署推荐系统离线部分](./offline)
- [部署推荐系统在线部分](./online)
- 
## API 概览 

此推荐系统的API共有三种：

- retrieve 
  
  `/retrieve/{userId}` - 获取用户的推荐商品列表 
  
- event
  
   `/event/portrait/{userId}` - 更新用户画像

   `/event/recall/{userId}`  - 触发用户召回

- admin
   
   `/event/start_train` - 触发离线训练任务和批量更新任务


API的swagger文档如下所示： 

![RS API overview](/images/rs-api-overview.png)

