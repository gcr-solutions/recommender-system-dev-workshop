---
title: 部署在线部分设施
weight: 3
---

在此步骤中，您将部署推荐系统**在线部分**基础设施

1. 进入/home/ec2-user/environment/recommender-system-dev-workshop-code/scripts目录

   ```sh
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   ```

2. 在左边栏打开 **eks/nodes-config.yaml** 文件，将 **metadata.region** 改为您目前的区域，默认为 ap-northeast-1 (Tokyo)。 **请注意**：如果您使用的是 us-east-1 (N.Virginia) 区域，则需要添加以下配置：
   
    `availabilityZones: ['us-east-1a', 'us-east-1b', 'us-east-1c', 'us-east-1d', 'us-east-1f']`
   
    ![change nodes config](/images/change-nodes-config.png)

   修改完后请保存。

3. 运行以下命令创建基础设施，包括：
   - eks cluster
   - istio
   - efs
   - elastic cache(redis)

   ```sh
   ./setup-rs-system.sh infra
   ```

   {{% notice info %}}
   这将需要大约 30 分钟来配置
   {{% /notice %}}

4. 验证已经成功创建的基础设施：

   - 检查 EFS 创建成功，控制台输出应如下所示：

   ![Verify EKS nodes](/images/check-efs.png)

   - 检查 ElasticCache（redis）创建成功，控制台输出如下：

   ![Verify EKS nodes](/images/check-redis.png)

   - 验证eks节点创建成功，应该有两个节点，节点状态应该是**Ready**

   ```sh
   kubectl get node
   ```

   ![Verify EKS nodes](/images/check-eks-nodes.png)