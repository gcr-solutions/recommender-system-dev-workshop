---
title: AWS Cloud9
weight: 1
---

AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. It includes a code editor, debugger, and terminal.

## Create new Cloud9 IDE environment

1. If you don’t already have an AWS account with Administrator access: [create one now by clicking here](https://aws.amazon.com/getting-started/)
2. Go to [AWS Cloud9 Console](https://ap-northeast-1.console.aws.amazon.com/cloud9)
3. Use the region drop list to select **Asia Pacific (Tokyo)ap-northeast-1**
4. Click **Create environment** button to create an cloud9 environment

![Create Cloud9 Environment](/images/create-cloud9-start.png)

5. Name it `gcr-rs-workshop`, click Next
6. Take all default values, click **Next step** and **Create environment**

{{% notice info %}}
This will take about 2 minutes to provision
{{% /notice %}}

When it comes up, the cloud9 console environment should looks like below:

![Cloud9 Welcome](/images/cloud9-welcome.png)

### Configure Cloud9 IDE environment

When the environment comes up, customize the environment by:

1 . Close the **welcome page** tab, close the **Quick Start** tab, close **lower work area** tab

![Cloud9 Close](/images/cloud9-close.png)

3 . Open a new **terminal** tab in the main work area.

![Cloud9 Open Terminal](/images/cloud9-open-terminal.png)


