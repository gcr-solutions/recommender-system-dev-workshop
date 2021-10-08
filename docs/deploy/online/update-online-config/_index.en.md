---
title: Update Config
weight: 4
---

In this step, you'll update online services config according to infrastructure created in previous steps.

1. Run the command below to update local config, including:

    - Elasticache(Redis) endpoint
    - AccountId
    - Region

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    ./setup-rs-system.sh config
    ```

2. Push your change to your CodeCommit repo through below command:

    ```sh
    git pull
    git add -A
    git commit -m "update config"
    git push
    ```