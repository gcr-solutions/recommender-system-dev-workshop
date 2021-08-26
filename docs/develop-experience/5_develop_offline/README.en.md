---
title: Develop Offline Of Recommender System
weight: 45
---

## Experience recall logic

###  Experience recall without `keywords`

1. Open recall log GUI

    ![recall argo log GUI](/images/recall-argo-log.png)

2. Click 4 ~ 5 news in the recommended list

    ![recommended list GUI](/images/rs-gui.png)

3. View recall log in argo GUI

    ![recall log without keywords](/images/recall-log-nokeywords.png)

###  Experience recall with `keywords`

1. Run below script to change recall config file:

    ```sh 
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./change-recall-config-offline.sh
    ```

    The old config file:

    ![recall config old](/images/recall-config-v1.png)

    The new config file:

    ![recall config new](/images/recall-config-v2.png)

    The recall config file has been changed and offline notified online to load new config file. Please click the [Step Function Link](https://console.aws.amazon.com/states/home#/statemachines), search `rs-dev-workshop-News-NotificationStepFunc` and wait the status become succeed.

    {{% notice info %}}
    Please wait about 4 minutes, make sure the execution of step functions `rs-dev-workshop-News-NotificationStepFunc` is complete
    {{% /notice %}}

2. Click 4 ~ 5 news in the recommended list again

    ![recommended list GUI](/images/rs-gui.png)

3. View recall log in argo GUI

    From the log, we can see that new config is loaded:

    ![recall log load new config file](/images/recall-log-loadfile.png)

    Recall with `keywords` is in the log:

    ![recall log with keywords](/images/recall-log-keywords.png)

