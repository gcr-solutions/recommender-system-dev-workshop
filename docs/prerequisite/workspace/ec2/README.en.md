---
title: Create AWS EC2
weight: 1
---

## Create new EC2 to deploy all the code

### Create key pair

1. Go to [Key pairs (ap-northeast-1 region)](https://ap-northeast-1.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-1#KeyPairs:) [Key pairs (cn-north-1 region)](https://console.amazonaws.cn/ec2/v2/home?region=cn-north-1#KeyPairs:)
2. Create a key pair: `gcr-rs-dev-workshop-ec2-key` 

  ![Key pairs](/images/ec2-key-pair.png)

  ![Create key pair](/images/ec2-key-pair-name.png)
   
3. Suppose you are using Mac, save the key pair to you local disk, eg: `~/Downloads`

4. Open an SSH client, run this command, to ensure your key is not publicly viewable
```sh
cd ~/Downloads

chmod 400 gcr-rs-dev-workshop-ec2-key.pem

```

## Create new EC2 instance

1. Go to [CloudFormation (ap-northeast-1 region)](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create/template) [CloudFormation (cn-north-1)](https://console.amazonaws.cn/cloudformation/home?region=cn-north-1#/stacks/create/template)

   CloudFormation template:`https://aws-gcr-rs-sol-workshop-ap-northeast-1-common.s3.ap-northeast-1.amazonaws.com/rs-dev-workshop-code/release/v1/rs-raw-ec2.yaml`

   ![EC2 CloudFormation ](/images/ec2-cf-s3url.png)

2. **Stack name**: `gcr-rs-dev-workshop-ec2`
   **KeyPairParam**: `gcr-rs-dev-workshop-ec2-key`
   
   ![EC2 CloudFormation Stack ](/images/ec2-cf-stackname.png)

3. Next -> Next -> Create Stack
  
   ![EC2 CloudFormation Create ](/images/ec2-cf-create.png)

4. Wait CloudFormation deployment complete
   
   {{% notice info %}}
   This will take about 2 - 3 minutes to provision
   {{% /notice %}}

5. Get CloudFormation output
   ![EC2 CloudFormation Output ](/images/ec2-cf-output.png)

6. Open an SSH client, connect to your instance, replace <EC2_IP_Address> with the EC2 IP

```shell

cd <Your_key_dir> # eg. cd ~/Downloads

HOST_IP=<EC2_IP_Address>
ssh -i "gcr-rs-dev-workshop-ec2-key.pem" ec2-user@${HOST_IP}

```

7. Type yes when showing the messages below.

   ![Connect-to-ec2](/images/connect-to-ec2.png)

8. Check your EC2 environment
```shell
echo "eksctl version"
eksctl version
echo "kubectl version --client"
kubectl version --client

aws configure get default.region

echo $REGION
```

{{% notice info %}}
   
if the information is empty, please run `tail /var/log/user-data.log` to check the init log, maker sure init script finished successfully,
then **re-login** the EC2.

{{% /notice %}}

