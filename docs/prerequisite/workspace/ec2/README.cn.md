---
title: 创建 EC2
weight: 1
---

## 创建一个 AWS EC2 机器，用来部署我们的代码

### 创建密钥对

1. 转到 [Key pairs](https://ap-northeast-2.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-2#KeyPairs:)
2. 创建密钥对: `gcr-rs-dev-workshop-ec2-key` 

  ![Key pairs](/images/ec2-key-pair.png)

  ![Create key pair](/images/ec2-key-pair-name.png)
   
3. 保存密钥对文件到本地目录, 例如: `~/Downloads`

4. 打开 SSH 客户端, 运行下面命令, 确保您的密钥对对他人不可见
```sh
cd ~/Downloads

chmod 400 gcr-rs-dev-workshop-ec2-key.pem

```

## 创建 EC2 实例

1. 转到 [CloudFormation (ap-northeast-1 区域)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=gcr-rs-dev-workshop-ec2&templateURL=https://aws-gcr-rs-sol-workshop-ap-northeast-1-common.s3.ap-northeast-1.amazonaws.com/rs-dev-workshop-code/release/v1/rs-raw-ec2.yaml
) 或者 [CloudFormation (cn-north-1)](https://console.amazonaws.cn/cloudformation/home?region=cn-north-1#/stacks/create/template?region=cn-north-1&stackName=gcr-rs-dev-workshop-ec2&templateURL=https://aws-gcr-rs-sol-workshop-cn-north-1-common.s3.cn-north-1.amazonaws.com.cn/rs-dev-workshop-code/release/v1/cn-rs-raw-ec2.yaml)

   CloudFormation 模版:

   - AWS 全球区域:
   ```   
    https://aws-gcr-rs-sol-workshop-ap-northeast-1-common.s3.ap-northeast-1.amazonaws.com/rs-dev-workshop-code/release/v1/rs-raw-ec2.yaml
   ```
   - AWS 中国区域:
   ``` 
    https://aws-gcr-rs-sol-workshop-cn-north-1-common.s3.cn-north-1.amazonaws.com.cn/rs-dev-workshop-code/release/v1/cn-rs-raw-ec2.yaml
   ```
   

   ![EC2 CloudFormation ](/images/ec2-cf-s3url.png)

2. **Stack 名字**: `gcr-rs-dev-workshop-ec2`
   **KeyPairParam**: `gcr-rs-dev-workshop-ec2-key`
   
   ![EC2 CloudFormation Stack ](/images/ec2-cf-stackname.png)

3. 点击按钮 "下一步" -> "下一步" -> "创建"
  
   ![EC2 CloudFormation Create ](/images/ec2-cf-create.png)

4. 等待部署完成
   
   {{% notice info %}}
   等待 2 - 3 分钟左右
   {{% /notice %}}

5. 检查 CloudFormation 输出

   ![EC2 CloudFormation Output ](/images/ec2-cf-output.png)

6. 打开 SSH 客户端, 链接刚才创建的 EC2 实例, 替换 <EC2_IP_Address> 为实际的 IP 地址
```shell

cd ~/Downloads
HOST_IP=<EC2_IP_Address>
ssh -i "gcr-rs-dev-workshop-ec2-key.pem" ec2-user@${HOST_IP}


```
7. 检查环境
```shell
echo "eksctl version"
eksctl version
echo "kubectl version --client"
kubectl version --client

aws configure get default.region
echo $REGION
```

{{% notice info %}}
   
假如上面的信息是空， 请运行 `tail /var/log/user-data.log` 检查 log，确保初始化脚本允许完成，然后**重新登录** EC2

{{% /notice %}}