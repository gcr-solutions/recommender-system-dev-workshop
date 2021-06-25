---
title: 创建 SSH 密钥
weight: 5
---

请运行此命令在 Cloud9 中生成 SSH 密钥。 如有必要，此密钥将用于工作节点实例以允许 ssh 访问。 

```sh
ssh-keygen
```

{{% notice tip %}}
按`回车` 3次以采用默认选择 
{{% /notice %}}

将公钥上传到您的 EC2 实例： 

```sh
aws ec2 import-key-pair --key-name "gcr-rs-workshop-key" --public-key-material file://~/.ssh/id_rsa.pub
```