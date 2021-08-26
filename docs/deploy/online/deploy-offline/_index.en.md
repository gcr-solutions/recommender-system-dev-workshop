---
title: Deploy The Offline Logic
weight: 2
---

1. Setup offline

    ``` 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh deploy-offline
    ```

2. Go to [AWS code build console](https://console.aws.amazon.com/codesuite/codebuild/projects)
, check your code build projects, search `rs-dev-workshop-offline-`,  make sure below projects are built successful.

    - `rs-dev-workshop-offline-lambda-build`
    - `rs-dev-workshop-offline-news-step-funcs-build`
    - `rs-dev-workshop-offline-news-inverted-list-build`

    ![Verify offline codebuild](/images/offline-code-build.png)

{{% notice info %}}
This will take about 5 minutes to provision
{{% /notice %}}







