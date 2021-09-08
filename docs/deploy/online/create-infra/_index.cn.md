---
title: 部署在线部分设施
weight: 3
---

在此步骤中，您将部署推荐系统**在线部分**基础设施

1. 运行以下命令创建基础设施，包括：
   - eks cluster
   - istio
   - efs
   - elastic cache(redis)
   
   ```sh
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   ./setup-rs-system.sh infra
   ```

   {{% notice info %}} 
   配置时间需要大约 30 分钟 
   {{% /notice %}}

2. 验证已经成功创建的基础设施：

   - 检查 EFS 创建成功，控制台输出应如下所示：

   ![Verify EKS nodes](/images/check-efs.png)

   - 检查 ElasticCache（redis）创建成功，控制台输出如下：

   ![Verify EKS nodes](/images/check-redis.png)

   - 验证eks节点创建成功，应该有两个节点，节点状态应该是**Ready**

   ```sh
   kubectl get node
   ```

   ![Verify EKS nodes](/images/check-eks-nodes.png)