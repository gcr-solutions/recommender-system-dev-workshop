---
title: 设置 Argo CD 服务器
weight: 5
---

在此步骤中，您将在 EKS 集群中设置 Argo CD 服务器

1. 跳转到/home/ec2-user/environment/recommender-system-dev-workshop-code/scripts目录

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ```

2. 运行以下命令在 eks 集群中设置 ArgoCd 服务器

   ```sh
   ./setup-rs-system.sh argo-server
   ```
   
   {{% notice info %}}
   这将需要大约 2 分钟的时间进行配置
   {{% /notice %}}

   控制台将输出 Argo CD 的**用户名**、**密码**和服务器**端点**，如下所示：

   ![Argocd password](/images/argocd-password.png)

   将 **端点URL** 内容复制到浏览器中，并访问 Argo CD 服务器网站。如果您是第一次访问此网站，请点击**Advanced**和**Proceed to...**

   ![Argocd First](/images/argocd-first.png)

   ![Argocd Second](/images/argocd-second.png)

   输入**用户名**和**密码**，然后点击**登录**，网站应该如下图所示：

   ![Argocd Signin](/images/argocd-signin.png)

   ![Argocd Second](/images/argocd-main-page.png)

恭喜您！Argo CD 服务器设置成功！！




