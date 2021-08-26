---
title: 创建 Argo CD 应用
weight: 6
---

在本节中，您将在 EKS 集群中创建 Argo CD 应用程序并部署所有在线服务

1. 进入/home/ec2-user/environment/recommender-system-dev-workshop-code/scripts目录

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ```

2. 运行以下命令来创建和部署在线部分：

    ```sh
    ./setup-rs-system.sh application
    ```

    大约 1 分钟后，控制台将显示如下消息：

    **application 'gcr-recommender-system-news-dev' created**

3. 访问 Argo CD 网站检查服务部署状态。 **请确保所有的状态都变成绿色后，再执行之后的步骤！！**： 

    ![Argocd application status](/images/argocd-app-status.png)

4. 将数据加载到系统中。

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./load-seed-data.sh
    ```

5. 获取 GUI 端点URL： 

    ```sh
    ./get-ingressgateway-elb-endpoint.sh
    ```

    通过端点URL访问应用网站，界面应该如下图所示： 

    ![Demo UI](/images/demo-ui.png)

恭喜你！ 推荐系统部署成功！！ 




