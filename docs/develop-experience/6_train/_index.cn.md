---
title: 更新行为模型
weight: 46
---

打开右上角的系统设置，您会看到三种离线功能： 

![Offline-Icon](/images/offline-icon.png)

随着推荐系统的运行，越来越多的行为数据被收集到系统中。重新训练你的行为模型是一个很好的做法，这样它就可以更准确地预测用户喜欢什么。为方便起见，此 workshop 已经设置了用于训练模型的参数。 如果您单击操作模型更新图标，您将看到图标变为灰色： 

![Action-Icon-Yellow](/images/action-icon-gray.png)


这意味着后台的相关函数已经启动。 

{{% notice info %}}
这将需要大约 15 分钟才能完成 
{{% /notice %}}

训练完成后，此图标将再次变为蓝色，并提示**执行成功**： 

![Action-Icon-Green](/images/action-icon-green.png)

如果训练时发生了错误，此图标将变为红色，您可以点击**查看详情**的链接来查明原因： 

![Action-Icon-URL](/images/action-icon-url.png)

当模型已经训练好后，离线服务会通知在线服务重新加载模型。 在此功能中，排名服务将被通知重新加载训练好的模型。 

另外两个离线功能将在下一页介绍。 


