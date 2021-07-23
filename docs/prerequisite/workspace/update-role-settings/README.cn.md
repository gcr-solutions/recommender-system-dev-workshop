---
title: 更新 IAM 设置
weight: 4
---

{{% notice info %}}
Cloud9 通常动态管理 IAM 凭证。 这当前与 EKS IAM 身份验证不兼容，因此我们需禁用该动态管理并改为依赖于 IAM 角色。
{{% /notice %}}

- 打开您的 Cloud9 工作区并单击齿轮图标（在右上角） 
- 选择 **AWS SETTINGS**
- 关闭 **AWS managed temporary credentials**
- 关闭设置

    ![Cloud9 Manage EC2 Instance](/images/cloud9-update-role-setting.png)

- 安装 jq 工具

    ```sh
    sudo yum -y install jq
    ```

- 为确保没有使用临时证书，我们还将删除所有现有的证书：

    ```sh
    rm -vf ${HOME}/.aws/credentials
    ```

- 将当前的区域作为默认区域, 并配置 aws cli。 

    ```sh
    export ACCOUNT_ID=$(aws sts get-caller-identity --output text --query Account)
    export AWS_REGION=$(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r '.region')
    export REGION=${AWS_REGION}
    ```

- 检查 AWS_REGION 是否设置为您当前区域:

    ```sh
    test -n "$AWS_REGION" && echo AWS_REGION is "$AWS_REGION" || echo AWS_REGION is not set
    ```

- 运行以下命令将相关数据保存到 bash_profile 文件:

    ```sh
    echo "export ACCOUNT_ID=${ACCOUNT_ID}" | tee -a ~/.bash_profile
    echo "export AWS_REGION=${AWS_REGION}" | tee -a ~/.bash_profile
    echo "export REGION=${AWS_REGION}" | tee -a ~/.bash_profile
    aws configure set default.region ${AWS_REGION}
    aws configure get default.region
    ```

### 验证 IAM 角色 

- 使用 [GetCallerIdentity](https://docs.aws.amazon.com/cli/latest/reference/sts/get-caller-identity.html) CLI 命令验证 Cloud9 IDE 是否使用正确的 IAM 角色。

    ```sh
    aws sts get-caller-identity --query Arn | grep gcr-rs-dev-workshop-admin -q && echo "IAM role valid" || echo "IAM role NOT valid"
    ```

    命令行应该显示 **IAM role valid** 。如果 IAM 角色无效，<span style="color: red;">**请不要继续进行**</span>， 返回并检查之前的步骤。 