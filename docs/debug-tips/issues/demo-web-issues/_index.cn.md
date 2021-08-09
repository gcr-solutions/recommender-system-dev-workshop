---
title: 浏览推荐系统
weight: 73
---

1. 如果登陆推荐系统演示网站后，出现 500 的错误， 请打开 Argo CD 网站，确保所有 Pod 创建成功。若有 Pod 失败，请查看该 Pod 的 log 信息， 如下所示：

    ![pod failed log](/images/pod-failed-log.png)

    若显示地区不对，请参考[调试：创建Argo CD应用](../deploy-argocd-application-issues)中的问题二，修改 config.yaml 文件中的地区。 若显示没有权限，请跳转到**创建 IAM 角色**步骤增加相应的权限。
