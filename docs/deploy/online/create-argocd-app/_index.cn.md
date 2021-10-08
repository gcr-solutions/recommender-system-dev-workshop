---
title: 创建 Argo CD 应用
weight: 6
---

在本节中，您将在 EKS 集群中创建 Argo CD 应用程序并部署所有在线服务

1. 运行以下命令来创建和部署推荐系统应用：

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh application >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

    大约 1 分钟后，控制台将显示如下消息：

    **application 'gcr-recommender-system-news-dev' created**

3. 访问 Argo CD 网站检查服务部署状态。 **请确保所有的状态都变成绿色后，再执行之后的步骤！！**： 

    ![Argocd application status](/images/argocd-app-status.png)

4. 将数据加载到系统中。

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh load-data >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

5. 获取 GUI 端点URL： 

    ```sh
    ./setup-rs-system.sh get-endpoint
    ```

   **注意**：若您部署的区域是中国区域，您将会看到以下命令，提示您创建 SSH 隧道。请复制 SSH 命令，在本地重新打开一个SSH 客户端，进入到保存密钥对的文件夹。粘贴并执行 SSH 命令。
   
   ![Create Tunnel](/images/create-tunnel-endpoint.png)
   
    通过端点URL访问应用网站，界面应该如下图所示： 

    ![Demo UI](/images/demo-ui.png)

恭喜你！ 推荐系统部署成功！！

   {{% notice info %}}
   管理员控制面板默认设置为定时自动计算，若您想节约成本，请打开[cloudwatch 控制面板](https://console.aws.amazon.com/events/home#/rules), 选中并关闭 `rs-dev-workshop-News-DashboardScheduledRule`。
   {{% /notice %}}

![Dashboard Schedule Disable](/images/dashboard-schedule-disable.png)




