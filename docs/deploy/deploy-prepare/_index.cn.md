---
title: 准备代码与部署脚本
weight: 1
---

在本节中，您需要复刻 [recommender-system-dev-workshop-code 仓库](https://github.com/gcr-solutions/recommender-system-dev-workshop-code) 并克隆到 Cloud9 工作区中。

1. 访问 [recommender-system-dev-workshop-code 仓库](https://github.com/gcr-solutions/recommender-system-dev-workshop-code) ，点击 **Fork** 按钮

    ![Fork Button](/images/fork-button.png)

2. 您的GitHub账号会增加 **recommender-system-dev-workshop-code** 仓库，链接应该是 https://github.com/您的github用户名/recommender-system-dev-workshop-code

   ![Fork Repo](/images/fork-repo.png)

3. 将仓库克隆到您的Cloud9工作区，请将 <your-github-username> 替换为您的Github用户名。

   ```sh
   cd /home/ec2-user/environment
   git clone git@github.com:<your-github-username>/recommender-system-dev-workshop-code.git
   cd recommender-system-dev-workshop-code/
   ```
