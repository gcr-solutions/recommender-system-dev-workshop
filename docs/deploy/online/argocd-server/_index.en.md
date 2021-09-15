---
title: Setup Argo CD Server
weight: 5
---

In this step, you will setup Argo CD server in EKS cluster

1. Run the below command to setup argocd server in eks cluster 
   
   ```sh
   cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
   nohup ./setup-rs-system.sh argo-server >> ~/nohup.log 2>&1 &
   tail -f ~/nohup.log 
   ```
    
   {{% notice info %}}
   This will take about 2 minutes to provision
   {{% /notice %}}

   **Attention**：If this workshop deployed in China Region，you will see the following output and mention you to create SSH Tunnel. Open a new SSH Client in your local environment and goto the Key Pair directory. Copy and Paste the following SSH Command.
   
   ![Create Tunnel](/images/create-tunnel-argocd.png)


   the console will output **user name**, **password** and server **endpoint** of argocd like below:

   ![Argocd password](/images/argocd-password.png)

   Copy **endpoint** into browser to access argocd server portal, if you are the first time to access this endpoint, click **Advanced** and **Proceed to ...**

   ![Argocd First](/images/argocd-first.png)

   ![Argocd Second](/images/argocd-second.png)

   Input **user name** and **password**, then click **SIGN IN**, the portal should looks like below:

   ![Argocd Signin](/images/argocd-signin.png)

   ![Argocd Second](/images/argocd-main-page.png)

The argo cd server setup successfully!!


