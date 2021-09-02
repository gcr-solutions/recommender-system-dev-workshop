---
title: Create secrets
weight: 2
---

In this section, you will create secretsmanager to store GitHub personal access token

1. If you don't have personal access token, please follow [creating-a-personal-access-token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) to create it. 

2. Save GitHub token to secretsmanager
```
cd /home/ec2-user/recommender-system-dev-workshop-code/scripts

GITHUB_TOKEN=<your_github_token>
GITHUB_USER=<your_github_user>

./setup-ssm.sh  $GITHUB_TOKEN $GITHUB_USER
 
```