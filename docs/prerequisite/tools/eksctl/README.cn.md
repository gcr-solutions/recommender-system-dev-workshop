---
title: 安装 eksctl
weight: 1
---


eksctl 是一个命令行工具，用于处理 EKS 集群，可自动执行许多单独的任务。 在此workshop中，您将使用 [eksctl](https://eksctl.io/introduction/#installation) 。 安装 eksctl 后，您就可以开始使用了。

在终端命令行下，输入以下两个命令： 

```sh
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin

```

这将在您的 **Cloud9** 环境中安装 `eksctl`。 要测试以确保命令安装正确，请执行以下命令： 

```
eksctl get cluster
```

您应该会收到 "**No clusters found**" 消息。 

```
eksctl version
```

您应该获得“**0.48.0**”或更高版本。 