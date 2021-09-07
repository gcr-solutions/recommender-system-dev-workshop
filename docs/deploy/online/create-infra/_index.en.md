---
title: Create Infrastructure
weight: 3
---

In this step, you will create Recommender System Online part infrastructure

1. Run the command below to create infrastructure, including:
   - eks cluster
   - istio
   - efs
   - elastic cache(redis)

   ```sh
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   ./setup-rs-system.sh infra
   ```

   {{% notice info %}}
   This will take about 30 minutes to provision
   {{% /notice %}}

2. Verify the infrastructre already created successfully:

   Check EFS created successfully, the console output should like below:

   ![Verify EKS nodes](/images/check-efs.png)

   Check elastic cache(redis) created successfully, the console output should like below:

   ![Verify EKS nodes](/images/check-redis.png)

   Verify eks nodes created successfully, there should be two nodes and status should be **Ready**

   ```sh
   kubectl get node
   ```
   
   ![Verify EKS nodes](/images/check-eks-nodes.png)