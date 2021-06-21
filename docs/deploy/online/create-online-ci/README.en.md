---
title: Create Online CI
weight: 1
---

In this step, you'll create AWS codebuild project to build services of Recommender System Online part, including `demo`,`event`,`filter`,`loader`,`portrait`,`rank`,`recall`,`retrieve`,`ui`.

1. Set your own configuration.
- In your cloud9 workspace, double click `online-code-build-setup.sh` file in the cloud9 left sidebar. It looks like below:
![Update Codebuild Config](/images/update-codebuild-config.png)

- Replace <github_user_name> with your github account user name.
![Update Codebuild Github user](/images/update-codebuild-github-user.png)

- Replace <github_access_token> with your github account personal access token. If you don't have personal access token, please follow [creating-a-personal-access-token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) to create it. 
![Update Codebuild Access Token](/images/update-codebuild-access-token.png)

- Save your change

2. Run ./online-code-build-setup.sh script to create codebuild projects

```sh
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./online-code-build-setup.sh
```

3. Go to [AWS Codebuild Console](https://ap-northeast-1.console.aws.amazon.com/codesuite/codebuild/home?region=ap-northeast-1) to check all services project have been created successfully.
picture

4. After a few minutes, all these projects should run successfully, if any project fails, please run it again.