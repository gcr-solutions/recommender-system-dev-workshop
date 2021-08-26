---
title: Create Infrastructure
weight: 3
---

In this step, you will create Recommender System Online part infrastructure

1. Go to /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts directory

   ```sh
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   ```

2. open **eks/nodes-config.yaml** file, and replace the **metadata.region** with your current region. The default value is ap-northeast-1 (Tokyo). **Attention**: If you are using the us-east-1 (N.Virginia) region, you need to add the following statement to the file:

    `availabilityZones: ['us-east-1a', 'us-east-1b', 'us-east-1c', 'us-east-1d', 'us-east-1f']`

   ![change nodes config](/images/change-nodes-config.png)

   Save the file.

3. Run the command below to create infrastructure, including:
   - eks cluster
   - istio
   - efs
   - elastic cache(redis)

   ```sh
   ./setup-rs-system.sh infra
   ```

   {{% notice info %}}
   This will take about 30 minutes to provision
   {{% /notice %}}

4. Verify the infrastructre already created successfully:

   Check EFS created successfully, the console output should like below:

   ![Verify EKS nodes](/images/check-efs.png)

   Check elastic cache(redis) created successfully, the console output should like below:

   ![Verify EKS nodes](/images/check-redis.png)

   Verify eks nodes created successfully, there should be two nodes and status should be **Ready**

   ```sh
   kubectl get node
   ```
   
   ![Verify EKS nodes](/images/check-eks-nodes.png)