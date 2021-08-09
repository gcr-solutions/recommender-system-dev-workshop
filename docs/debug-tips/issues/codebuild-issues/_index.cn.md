---
title: 构建CodeBuild
weight: 74
---

1. 如果您在构建 Codebuild 时出现 **assembled-train-model-build** 的错误，如下图所示：

   ![assembled-train-model failed log](/images/assembled-train-model-failed-log.png)

   原因是因为您的Github账号fork的仓库的版本未更新，请更新您的Github仓库，并重新构建CodeBuild。