---
title: Setup Argo cd Server
weight: 2
---

In this step, you will setup Argo CD server in EKS cluster

1. Go to /home/ec2-user/environment/recommender-system-solution/scripts directory

```sh
cd /home/ec2-user/environment/recommender-system-solution/scripts
```

2. Run the below command to setup argocd server in eks cluster 

```sh
./setup-argocd-server.sh
```
{{% notice info %}}
This will take about 1 minutes to provision
{{% /notice %}}

the console will output **user name**, **password** and server **endpoint** of argocd like below:

![Argocd password](/images/argocd-password.png)


Copy **endpoint** into browser to access argocd server portal, if you are the first time to access this endpoint, click **Advanced** and **Proceed to ...**

![Argocd First](/images/argocd-first.png)

![Argocd Second](/images/argocd-second.png)

Input **user name** and **password**, then click **SIGN IN**, the portal should looks like below:

![Argocd Signin](/images/argocd-signin.png)

![Argocd Second](/images/argocd-main-page.png)

The argo cd server setup successfully!!



