---
title: Recommender System Solution workshop 
chapter: true
---

# GCR Recommender System Solution

Amazon Recommender System Solution is a cloud-native recommendation solution for different scenarios. This solution is suitable for customers with needs for building the recommender systems in different scenarios, like news, movies, TV, travelings, education and so on. This solution is designed with both flexibility and integrity. No matter you just start to build a recommender system or on the way , you can use this solution to speed up the process, save time and cost from the complete-system perspective. It is an open-source project in GitHub, anyone can contribute to features or adding more related solutions.

![What is Recommender System](/images/what-is-recsys.png)

### Recommender System Solution will build a cloud-native recommender system for you from three aspects 

#### Online Services

The core services of the recommender system are constructed using Amazon EKS, including user portrait, data loader, event notice, recall, rank, filter and so on. Some services will interact with redis. This design provides the customers with online service the recommender system based on microservice architecture.
#### Offline Logic

The offline logic is implemented using AWS Step Functions and Amazon Sagemaker. This includes data preprocess, model training, model validation, batch process and so on. Whenever new files or models are generated, the online services will be noticed to reload.

#### End-to-end Development

The CI/CD of system is implemented using AWS CodeBuild and Argo CD. This design helps the customers deploy the latest software into the production environment.