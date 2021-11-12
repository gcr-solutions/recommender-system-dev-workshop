---
title: Deploy Offline
weight: 2
---

1. Setup offline

    ```sh 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh deploy-offline >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

2. Go to [AWS code build console](https://console.aws.amazon.com/codesuite/codebuild/projects)
, check your code build projects, search `rs-dev-workshop-offline-`,  make sure all projects are built successful.

   {{% notice info %}}
   This will take about 20 minutes to provision
   {{% /notice %}}

   ![Offline CodeBuild Success](/images/offline-codebuild-success.png)








