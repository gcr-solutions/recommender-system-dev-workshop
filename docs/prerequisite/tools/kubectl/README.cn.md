---
title: 安装 Kubectl
weight: 2
---

Kubernetes 命令行工具 [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux) 允许您针对 Kubernetes 集群运行命令。 您可以使用 kubectl 来部署应用程序、检查和管理集群资源以及查看日志。 

在终端命令提示符下，输入以下两个命令： 

```sh
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

```

这将在您的 **Cloud9** 环境中安装 `kubectl`。 要测试以确保命令安装正确，请执行以下命令： 

```
kubectl version --client
```

您应该会看到 `kubectl` 版本消息。 
![kubectl version](/images/kubectl-version.png)