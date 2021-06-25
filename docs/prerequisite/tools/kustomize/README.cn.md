---
title: 安装 kustomize
weight: 23
---

## 安装 Kustomize

[Kustomize](https://github.com/kubernetes-sigs/kustomize) 可让您自定义原始、无模板的 YAML 文件以用于多种用途，而原始 YAML 文件保持不变并可按原样使用。 

Linux 下安装 kustomize： 

```sh
curl --silent --location --remote-name \
"https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize/v3.2.3/kustomize_kustomize.v3.2.3_linux_amd64" && \
chmod a+x kustomize_kustomize.v3.2.3_linux_amd64 && \
sudo mv kustomize_kustomize.v3.2.3_linux_amd64 /usr/local/bin/kustomize

```

使用以下命令验证安装：

```sh
kustomize version
```
您应该会看到如下消息： 
![kustomize version](/images/kustomize-version.png)