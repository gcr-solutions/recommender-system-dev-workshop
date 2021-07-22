---
title: Cleanup
weight: 60
---

Hopefully you’ve enjoyed the workshop and learned a few new things. Now follow these steps to make sure everything is cleaned up.

1. In the Cloud9 IDE Console, run below command to delete online:
```sh
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./clean-online.sh
```

{{% notice info %}}
This will take about 20 minutes to release resources
{{% /notice %}}

2. offline cleanup

``` 
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./clean-offline.sh
```

**Attention**: After you finish the above steps, the online and offline parts of the recommendation system have been cleaned. If you want to completely empty all resources, you need to perform the following steps: 

3. In the [Cloud9 Console](https://ap-northeast-1.console.aws.amazon.com/cloud9/home?region=ap-northeast-1#), select gcr-rs-dev-workshop env and click Delete button

4. Go to [IAM Role Console](https://console.aws.amazon.com/iam/home#/roles), select `gcr-rs-dev-workshop-admin` role, and delete this role.

5. Go to [EC2 Key Pairs](https://ap-northeast-1.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-1#KeyPairs:search=gcr-rs-dev-workshop-key), select `gcr-rs-dev-workshop-key`, and delete it.

6. Open your Github account, click **Settings** in the recommended system repository you forked, find the **Webhooks** column and delete all resources. Then delete your forked repo.

