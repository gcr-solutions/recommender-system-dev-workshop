---
title: Browse The Recommender System
weight: 73
---

1. If a 500 error occurs after logging in to the demo website of the recommendation system, please open the Argo CD website to ensure that all Pods created successfully. If a Pod fails, please check the log information of this Pod, as shown below:

    ![pod failed log](/images/pod-failed-log.png)

    If the displayed region is incorrect, please refer to [Debug: Create Argo CD Application](../deploy-argocd-application-issues) to modify the region in the **config.yaml** file. If it shows that there is no permission, please go to the **Create IAM Role** step to add the corresponding permission.

