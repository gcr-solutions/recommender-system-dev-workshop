---
title: Setup GitHub Account In Cloud9 Workspace
weight: 6
---

1. Set up git with your username and email through following commands, please replace `Your name here` and `your_email@example.com` with your Github account.

    ```git config --global user.name "Your name here" ```

    ```git config --global user.email "your_email@example.com" ```

2. Set up ssh on your cloud9 workspace.

    Enter the following command to check if you have files `~/.ssh/id_rsa` and `~/.ssh/id_rsa.pub`.
    
    ```sh
    ls ~/.ssh
    ```
  
    If you do not have, please follow [Create an SSH key](https://gcr-solutions.github.io/recommender-system-dev-workshop/prerequisite/workspace/create-ssh-key/readme/) to create such public/private keys.

    Enter the following command and **copy** to your clipboard.

    ```shell
    cat ~/.ssh/id_rsa.pub
    ``` 

3. Paste your ssh public key into your github account settings.
    - Go to your GitHub [Account Settings](https://github.com/settings/profile)
    - Click [SSH and GPG keys](https://github.com/settings/keys) in the left sidebar.
    - Click **New SSH key** on the top right.

    ![Github SSH New](/images/github-ssh-new.png)

    - Add a title (like “My Cloud9”) and paste the public key into the key text box.

    ![Paste Github SSH key](/images/paste-github-ssh-key.png)

4. Test your configuration through the following command:
    ```sh
    ssh -T git@github.com
    ```

    Type `yes` and press `enter`.

    If it says something like the following, it worked:
    
    `Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.`


