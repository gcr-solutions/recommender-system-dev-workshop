---
title: Switch to Amazon Personalize Method (To Be Released)
weight: 48
---

This feature will be launched soon, you can change the CloudFormation template to the following link to experience the internal beta version:

Global Region：
```shell
https://aws-gcr-rs-sol-workshop-ap-northeast-1-common.s3.ap-northeast-1.amazonaws.com/rs-dev-workshop-code/github/develop/v1.2/rs-raw-ec2.yaml
```

China (Beijing) Region：
```shell
https://aws-gcr-rs-sol-workshop-cn-north-1-common.s3.cn-north-1.amazonaws.com.cn/rs-dev-workshop-code/github/develop/v1.2/cn-rs-raw-ec2.yaml
```

Amazon Personalize is a fully managed personalized recommendation service that includes a variety of algorithms. These algorithms based on more than 20 years of personalization experience and development expertise in Amazon's retail business. The GCR Recommendation System provides three suggestions to use Amazon Personalize. You can switch to different mode with only one command, compare their recommendation results, and choose the most suitable recommendation system plan for your current business. The three plans shown in the following table:

|Plan |Amazon Personalize Recipe | Description | Alias |
|--- |--- | --- | --- |
|Complete Substitution|aws-user-personalization |If you only want to use the Amazon Personalize Service to achieve personalized recommendations for users, then you can adopt this plan. The online part of this plan provides actual use cases of Amazon Personalize Service, and the offline part provides automated processes of three functions: Model Update, New Item Addition, and New User Addition. This plan can greatly speed up your time to get started and deploy the Amazon Personalize Service.|ps-complete|
|Rank Model Substitution|aws-personalized-ranking |The existing ranking model of the GCR Recommendation System is the DKN model based on the knowledge graph. If you want to use the ranking model provided by Amazon Personalize, you can adopt this plan. The online part of this plan replaces the DKN model of the ranking module with the aws-personalized-ranking model. On the basis of the original process, the offline part adds the model training and data set import process of the Amazon Personalize service, and replaces the model with the aws-personalized-ranking model in the rank batch.|ps-rank|
|One Way Recall Logic|aws-sims |The existing recall model of the GCR Recommendation System contains four-way recall logic. If you want to use the item similarity model provided by Amazon Personalize as the fifth recall logic, you can adopt this plan. In the online part of this plan, one more recall logic provided by Amazon Personalize is added to the recall module. On the basis of the original process, the offline part adds the model training and data set import process of the Amazon Personalize service, and adds the recall logic implemented by aws-sims to the recall batch. |ps-sims|

If you want to switch to the **Complete Substitution**, execute the following command:
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh ps-complete
```

After execution, ArgoCD will deploy services in 3 minutes. Open the Argo CD website, you will see that containers are synchronizing and updating. If not, please click **REFRESH**. This process takes about 1 minute.

![Argo CD Sync](/images/argocd-sync-method.png)

After the synchronization is complete, open the Demo Website. At this time, the Recommendation System has been changed to retrieve the results entirely from the Amazon Personalize Service. Click the **Recommendation** button, and open the logs of the Retrieve Pod on the Argo CD website. You can see the newest recommendation list contains **ps-complete** description, which means that the Amazon Personalize Service provides the recommendation list.

![ps complete log](/images/ps-complete-result.png)

If you want to switch to the **Rank Model Substitution**, execute the following command:
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh ps-rank
```

After execution, open the Argo CD website and wait for the synchronization to complete.

Open the Demo Website, at this time the Recommendation System has been changed to use aws-personalized-ranking model rather than DKN model for ranking process. Click three news, and open the logs of the Rank Pod on the Argo CD website. You can see the ranking result contains the word **ps-rank**.

![ps rank log](/images/ps-rank-result.png)

If you want to switch to the **One Way Recall Logic**, execute the following command:
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh ps-sims
```

After execution, open the Argo CD website and wait for the synchronization to complete.

Open the Demo Website. At this time, the Recommendation system has added one more recall logic implemented by aws-sims to recall service. Click three news, and open the logs of the Recall Pod on the Argo CD website. You can see the recall result contains the word **ps-sims**.

![ps sims log](/images/ps-sims-result.png)

If you want to return to the **customize** method, just execute the following command and refresh the Argo CD:
```shell
cd /home/ec2-user/environment/recommender-system-dev-workshop-code/scripts
./change-method.sh customize
```


## How to switch method（optional）

If you have interests in understanding more about the process behind switching method, you can check the following content. 

After you execute the change-method.sh, you will see the following output in your terminal:

![change method output](/images/change-method-output.png)

The change-method.sh script has the following steps:

1. Update the solution name and campaign name in the config file (ps_config.json) by the input variable **METHOD**. 
   
2. Update the Latest Version ID in the config file (ps_config.json) from the Amazon Personalize Service.

3. Synchronize the new config file to the AWS S3 Service.

4. Notify the online loader service to download the latest config file from S3.

5. Update the METHOD variable in the EKS ConfigMap. Commit the change and push to the repository in the AWS CodeCommit Service.

After execution, Argo CD will synchronize the service automatically. The process is as following:

![change method process](/images/change-method-process.png)

