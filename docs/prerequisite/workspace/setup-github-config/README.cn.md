---
title: 在 Cloud9 中设置 GitHub 账户
weight: 6
---

1. 输入以下命令来配置git，请将`姓名`和`电子邮箱`替换为您的Github帐户信息。

    ```git config --global user.name "姓名" ```

    ```git config --global user.email "电子邮箱" ```

2. 在 cloud9 上设置 ssh。
   
    输入以下命令检查您是否有文件 `~/.ssh/id_rsa` 和 `~/.ssh/id_rsa.pub`。 
    ```sh
    ls ~/.ssh
    ```
    如果没有，请按照 [创建 SSH 密钥](https://gcr-solutions.github.io/recommender-system-dev-workshop/prerequisite/workspace/create-ssh-key/readme/) 来创建公钥与私钥。
   
    输入以下命令并**复制**命令行的输出(公钥)：
   
    ```sh
    cat ~/.ssh/id_rsa.pub
    ```

3. 将 ssh 公钥粘贴到您的 GitHub 帐户中。
   
   - 打开您的 GitHub 账户 中的 [Account Settings](https://github.com/settings/profile)
   - 单击左侧栏中的 [SSH and GPG keys](https://github.com/settings/keys) 。
   - 点击右上角的**New SSH key**。
     
   ![Github SSH New](/images/github-ssh-new.png)

   - 输入密钥名（如“My Cloud9”）并将公钥粘贴到文本框中。
     
   ![Paste Github SSH key](/images/paste-github-ssh-key.png)

4. 通过以下命令测试您的配置：
    ```sh
    ssh -T git@github.com
    ```
    输入 `yes` 并按 `回车`.

    如果命令行输出为以下内容，则配置成功：

    `Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.`


