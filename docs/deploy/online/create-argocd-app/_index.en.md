---
title: Create Argo CD application
weight: 6
---

In this step, you will create Argo CD application to deploy all online services into EKS cluster

1. Run below command to create and deploy application:

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./setup-rs-system.sh application > ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

    After about 1 minutes, the console will message as below:

    **application 'gcr-recommender-system-news-dev' created**

2. Access argo cd portal to check services deployment status. **Please make sure all the heart status become green and all the rotating tags become stable!!**:

    ![Argocd application status](/images/argocd-app-status.png)

3. Load the seed data into the system. Go to /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts directory

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./load-seed-data.sh > ~/nohup.log 2>&1 &
    tail -f ~/nohup.log 
    ```

4. Get the GUI endpoint:

    ```sh
    ./get-ingressgateway-elb-endpoint.sh
    ```

    Access ui through browser, it should like below:

    ![Demo UI](/images/demo-ui.png)

Congratulations!!! The recommender system has been deployed successfully!!
**Attention**: The default setting of Dashboard scheduled to automatic calculation. If you want to save costs, please open [cloudwatch control panel](https://console.aws.amazon.com/events/home#/rules), select and disable `rs -dev-workshop-News-DashboardScheduledRule`.

![Dashboard Schedule Disable](/images/dashboard-schedule-disable.png)

