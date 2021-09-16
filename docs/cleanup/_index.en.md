---
title: Cleanup
weight: 60
---

Hopefully you’ve enjoyed the workshop and learned a few new things. Now follow these steps to make sure everything is cleaned up.

1. In the terminal, run below command to delete online:
    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./clean-online.sh >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log
    ```
   
   {{% notice info %}}
   This will take about 20 minutes to release resources
   {{% /notice %}}

2. offline cleanup

    ```sh
    cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
    nohup ./clean-offline.sh >> ~/nohup.log 2>&1 &
    tail -f ~/nohup.log
    ```
   
   {{% notice info %}}
    After you finish the above steps, the online and offline parts of the recommendation system have been cleaned. If you want to completely empty all resources, you need to perform the following steps: 
   {{% /notice %}}

3. Go to [IAM Role Console](https://console.aws.amazon.com/iam/home#/roles), select the role beginning with `gcr-rs-dev-workshop-ec2` and delete it.

![GCR RS DEV](/images/gcr-rs-dev.png)

4. In the [Cloudformation Console](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/), delete below stacks:

    - `gcr-rs-dev-workshop-ec2` 
    - `rs-dev-workshop-codebuild-role-stack`


5. Go to [EC2 Key Pairs](https://console.aws.amazon.com/ec2/v2/home#KeyPairs:search=gcr-rs-dev-workshop-key), select `gcr-rs-dev-workshop-key`, and delete it.

6. Suppose you are using Mac, go to your local disk which saves the key, eg: `~/Downloads`

```
cd ~/Downloads
rm -f gcr-rs-dev-workshop-ec2-key.pem
```
