---
title: 创建在线 CodeBuild 项目
weight: 1
---

在此步骤中，您将创建 AWS CodeBuild 项目来构建推荐系统**在线部分**的服务，包括 **demo**、**event**、**filter**、**loader**、**portrait**、**rank**、**recall**、**retrieve**、**ui**。

1. 设置您的 CodeBuild 配置。
- 在您的 cloud9 工作区中，双击 Cloud9 左侧栏中的`setup-rs-system.sh`文件，如下图所示：
  
    ![Update Codebuild Config](/images/update-codebuild-config.png)

- 将 <github_user_name> 替换为您的 Github 帐户用户名。
  
    ![Update Codebuild Github user](/images/update-codebuild-github-user.png)

- 将 <github_access_token> 替换为您的 Github 帐户个人访问令牌。 如果您没有个人访问令牌，请先点击 [链接](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) 创建个人访问令牌。
  
    ![Update Codebuild Access Token](/images/update-codebuild-access-token.png)

- 保存您的更改

2. 运行以下命令创建在线CodeBuild项目

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh online-codebuild
    ```
   
{{% notice info %}}
这将需要大约 10 分钟进行配置
{{% /notice %}}

3. 进入[AWS Codebuild 控制台](https://console.aws.amazon.com/codesuite/codebuild/home) 查看并确保所有的项目已经创建成功。
   
    ![Codebuild Created](/images/codebuild-created.png)

4. 几分钟后，**gcr-rs-dev-workshop-recall-build** 和 **gcr-rs-dev-workshop-filter-build** 应该像下面这样成功运行（为了节省时间，我们刚刚触发了召回和过滤服务的构建）。 **如果任何项目失败，请重新运行。**
   
    ![Codebuild Succeed](/images/codebuild-successfully.png)
