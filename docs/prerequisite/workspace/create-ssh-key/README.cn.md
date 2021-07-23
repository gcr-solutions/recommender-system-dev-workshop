---
title: 创建 SSH 密钥
weight: 5
---

运行以下命令在 Cloud9 中生成 SSH 密钥，此密钥将允许以 ssh 方式访问工作节点实例。

```sh
ssh-keygen
```

{{% notice tip %}}
按`回车` 3次以采用默认选择 
{{% /notice %}}

将公钥上传到您的 EC2 实例： 

```sh
aws ec2 import-key-pair --key-name "gcr-rs-dev-workshop-key" --public-key-material file://~/.ssh/id_rsa.pub
```