---
title: Create Online Code Build Projects
weight: 1
---

In this step, you'll create AWS CodeBuild project to build services of Recommender System Online part, including **demo**, **event**, **filter**, **loader**, **portrait**, **rank**, **recall**, **retrieve**, **ui**.

1. Set your own configuration.
- In your cloud9 workspace, double click `setup-rs-system.sh` file in the cloud9 left sidebar. It looks like below:
  
    ![Update Codebuild Config](/images/update-codebuild-config.png)

- Replace <github_user_name> with your github account user name.

    ![Update Codebuild Github user](/images/update-codebuild-github-user.png)

- Replace <github_access_token> with your github account personal access token. If you don't have personal access token, please follow [creating-a-personal-access-token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) to create it. 

    ![Update Codebuild Access Token](/images/update-codebuild-access-token.png)

- Save your change

2. Run the following command to create online codebuild projects

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh online-codebuild
    ```
    
{{% notice info %}}
This will take about 10 minutes to provision
{{% /notice %}}

3. Go to [AWS Codebuild Console](https://console.aws.amazon.com/codesuite/codebuild/home) to check all services project have been created successfully.
    ![Codebuild Created](/images/codebuild-created.png)

4. After a few minutes, **gcr-rs-dev-workshop-recall-build** and **gcr-rs-dev-workshop-filter-build** should run successfully like below(For saving time, we just trigger recall and filter services build). **If any project fails, please run it again.**
    ![Codebuild Succeed](/images/codebuild-successfully.png)
