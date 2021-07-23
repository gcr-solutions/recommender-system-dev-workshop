---
title: Prepare code and deploy scripts
weight: 1
---

In this section, you'll need to fork a github repo from [recommender-system-dev-workshop-code repo](https://github.com/gcr-solutions/recommender-system-dev-workshop-code) and clone repo to cloud9 workspace.

1. Access [recommender-system-dev-workshop-code repo](https://github.com/gcr-solutions/recommender-system-dev-workshop-code), click **Fork** button

    ![Fork Button](/images/fork-button.png)

2. You should get a **recommender-system-dev-workshop-code** repo in your user account. The repo link should be https://github.com/your-github-username/recommender-system-dev-workshop-code

    ![Fork Repo](/images/fork-repo.png)

3. Clone repo to your cloud9 workspace, please replace <your github username> with your Github username.

    ```sh
    cd /home/ec2-user/environment
    git clone git@github.com:<your github username>/recommender-system-dev-workshop-code.git
    cd recommender-system-dev-workshop-code/
    ```
