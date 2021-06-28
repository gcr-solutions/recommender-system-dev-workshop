---
title: AWS Cloud9
weight: 1
---

AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. It includes a code editor, debugger, and terminal.

## Create new Cloud9 IDE environment

1. Go to [AWS Cloud9 Console](https://ap-northeast-1.console.aws.amazon.com/cloud9)
2. Use the region drop list to select **Asia Pacific (Tokyo)ap-northeast-1**
3. Click **Create environment** button to create an cloud9 environment

![Create Cloud9 Environment](/images/create-cloud9-start.png)

4. Name it `gcr-rs-dev-workshop`, click **Next**
5. Take all default values, click **Next step** and **Create environment**

{{% notice info %}}
This will take about 2 minutes to provision
{{% /notice %}}

When it comes up, the cloud9 console environment should looks like below:

![Cloud9 Welcome](/images/cloud9-welcome.png)

### Configure Cloud9 IDE environment

When the environment comes up, customize the environment by:

1 . Close the **welcome page** tab, close the **Quick Start** tab, close **lower work area** tab

![Cloud9 Close](/images/cloud9-close.png)

2 . Open a new **terminal** tab in the main work area.

![Cloud9 Open Terminal](/images/cloud9-open-terminal.png)

3 . Keep the AWS Cloud9 IDE opened in a browser tab throughout this workshop as we’ll use it for activities like using the AWS CLI and running Bash scripts.

