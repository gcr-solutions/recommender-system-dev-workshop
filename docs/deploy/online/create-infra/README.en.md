---
title: Create Infrastructure
weight: 1
---

In this step, you will create Recommender System Online part infrastructure

1. Go to /home/ec2-user/environment/recommender-system-solution/scripts directory

```sh
cd /home/ec2-user/environment/recommender-system-solution/scripts
```

2. Run the command below to create infrastructure, including:
- eks cluster
- istio
- efs
- elastic cache(redis)

```sh
./create-online-infra.sh
```

{{% notice info %}}
This will take about 20 minutes to provision
{{% /notice %}}

3. Verify the infrastructre already created successfully:

Check EFS created successfully, the console output should like below:

![Verify EKS nodes](/images/check-efs.png)

Check elastic cache(redis) created successfully, the console output should like below:

![Verify EKS nodes](/images/check-redis.png)

Verify eks nodes created successfully, there should be two nodes and status should be **Ready**
```sh
kubectl get node
```
![Verify EKS nodes](/images/check-eks-nodes.png)