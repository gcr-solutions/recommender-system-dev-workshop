---
title: Improve Continuously
weight: 46
---

The recommender system implements continuous deployment through the argo cd. This section includes following steps:
1. Change docker image tag in kustomization.yaml
2. Sync kustomization.yaml to argo cd.
3. Check new docker image has been deployed

Change docker image tag:
```sh
cd /home/ec2-user/environment/recommender-system-solution/manifests

sed -i 's/latest/'cd-test'/g' kustomization.yaml
```

Sync kustomization.yaml to argo cd

```sh
argocd app sync gcr-recommender-system --local /home/ec2-user/environment/recommender-system-solution/manifests
```

Check new docker image has been deployed, you should check argo cd, the services should be deployed again:

![CD Test](/images/cd-test.png)




