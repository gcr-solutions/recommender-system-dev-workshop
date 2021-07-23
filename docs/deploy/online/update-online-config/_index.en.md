---
title: Update Config
weight: 4
---

In this step, you'll update online services config according to infrastructure created in previous steps.

1. Go to /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts directory

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ```

2. Run the command below to update local config, including:

    - Elasticache(Redis) endpoint
    - AccountId
    - Region

    ```sh
    ./setup-rs-system.sh config
    ```

3. Push your change to your github repo through below command:

    ```sh
    git pull
    git add ../manifests/envs/news-dev/config.yaml
    git commit -m "update config"
    git push
    ```