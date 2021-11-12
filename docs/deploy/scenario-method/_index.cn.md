---
title: 选择场景和方法
weight: 1
---

1. 选择您想要部署的推荐场景与推荐方式。 首先输入以下命令，修改 `setup-rs-system.sh` 脚本中的环境变量：

   ```shell
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   vim setup-rs-system.sh
   ```

   将 SCENARIO 变量的值设置为您想要部署的推荐场景，可设置为 `news` 或 `movie`。将 METHOD 变量的值设置为您想要部署的推荐方式，可设置为 `customize`、`ps-complete` 、 `ps-rank` 、 `ps-sims` 。保存修改后的脚本。
