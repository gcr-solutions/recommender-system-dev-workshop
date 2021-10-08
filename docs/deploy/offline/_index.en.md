---
title: Deploy Offline
weight: 1
---

1. Choose the recommendation scenario and method. Enter the following command to update the environment variables in the `setup-rs-system.sh` file.

   ```shell
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   vim setup-rs-system.sh
   ```

   Set SCENARIO value to `news` or `movie`. Set METHOD value to `customize` or `ps-complete` or `ps-rank` or `ps-sims`, and save the file.

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








