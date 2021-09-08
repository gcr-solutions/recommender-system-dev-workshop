---
title: Deploy Offline
weight: 1
---

1. Setup offline

    ```sh 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh deploy-offline
    ```

2. Go to [AWS code build console](https://console.aws.amazon.com/codesuite/codebuild/projects)
, check your code build projects, search `rs-dev-workshop-offline-`,  make sure all projects are built successful.

{{% notice info %}}
This will take about 10 minutes to provision
{{% /notice %}}

   ![offline codebuild](/images/offline-codebuild.png)








