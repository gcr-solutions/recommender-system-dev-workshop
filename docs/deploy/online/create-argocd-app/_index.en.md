---
title: Create Argo CD application
weight: 6
---

In this step, you will create Argo CD application to deploy all online services into EKS cluster

1. Go to /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts directory

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ```

2. Run below command to create and deploy online part:=

    ```sh
    ./setup-rs-system.sh application
    ```

    After about 1 minutes, the console will message as below:

    **application 'gcr-recommender-system-news-dev' created**

3. Access argo cd portal to check services deployment status. **Please make sure all the heart status become green and all the rotating tags become stable!!**:

    ![Argocd application status](/images/argocd-app-status.png)

4. Load the seed data into the system. Go to /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts directory

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./load-seed-data.sh
    ```

5. Get the GUI endpoint:

    ```sh
    ./get-ingressgateway-elb-endpoint.sh
    ```

    Access ui through browser, it should like below:

    ![Demo UI](/images/demo-ui.png)

Congratulations!!! The recommender system has been deployed successfully!!




