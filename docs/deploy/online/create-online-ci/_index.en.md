---
title: Create Online CodeBuild
weight: 1
---

In this step, you'll create AWS CodeBuild project to build services of Recommender System Online part, including **demo**, **event**, **filter**, **loader**, **portrait**, **rank**, **recall**, **retrieve**, **ui**.

1. Run the following command to create online codebuild projects

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh online-codebuild
    ```
    
{{% notice info %}}
This will take about 10 minutes to provision
{{% /notice %}}

2. Go to [AWS Codebuild Console](https://console.aws.amazon.com/codesuite/codebuild/home) to check all services project have been created successfully. **If any project fails, please run it again.**
   
    ![Codebuild Succeed](/images/codebuild-successfully.png)
