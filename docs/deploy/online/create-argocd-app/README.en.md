---
title: Create Argo cd application
weight: 3
---

In this step, you will create Argo CD application to deploy all online services into EKS cluster

1. Go to /home/ec2-user/environment/recommender-system-solution/scripts directory

```sh
cd /home/ec2-user/environment/recommender-system-solution/scripts
```

2. Run below command to create and deploy online part:=

```sh
./create-argocd-application.sh
```

After about 1 minutes, the console will output as below:

![Argocd create application](/images/argocd-create-app.png)

3. Access argo cd portal to check services deployment status. **Please make sure all the heart status become green and all the rotating tags become stable!!**:

![Argocd application status](/images/argocd-app-status.png)

4. Load the seed data into the system. Go to /home/ec2-user/environment/recommender-system-solution/scripts directory

```sh
cd /home/ec2-user/environment/recommender-system-solution/scripts
```

```sh
./load-seed-data.sh
```

5. Get the GUI endpoint:

```sh
./get-ingressgateway-elb-endpoint.sh
```

Access ui through browser, it should like below:

![Demo UI](/images/demo-ui.png)

Congratulations!!! The recommender system has been deployed successfully!!




