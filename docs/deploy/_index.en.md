---
title: Deploy GCR Recommender System 
weight: 30
---

In this module, we will deploy **GCR Recommender System**


You’ll need the following steps:

- [Prepare deploy scripts](./deploy-prepare/readme)
- [Deploy Recommender System Offline](./offline/readme)
- [Deploy Recommender System Online](./online/)

## API Overview 

There are three types of API
- retrieve 
  
  `/retrieve/{userId}` - get the recommended item list for a user
  
- event
  
   `/event/portrait/{userId}` - trigger portrait update for a user

   `/event/recall/{userId}`  - trigger recall for a user

- admin
   
   `/event/start_train` - trigger offline training job
  
   `/event/batch_update` - trigger offline batch job, re-generating recommended item list for all users


The swagger description of the API is shown as below:

![RS API overview](/images/rs-api-overview.png)

