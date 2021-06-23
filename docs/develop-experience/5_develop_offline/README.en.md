---
title: Develop Offline of Recommender System TODO from Liuyong
weight: 45
---

1. Update below file 
``` 
src/offline/news/inverted-list/src/inverted-list.py
```

line 268-269, change two lines as below
``` python
    df_update.loc[df_update.new == 1, 'popularity'] = 10.0
    df_update.loc[df_update.new == 1, 'new'] = 0
```

2. commit your code

3. run code build to build new docker image 
   
    Go to codebuild project `rs-dev-workshop-offline-news-inverted-list-build`, start codebuild for that project.
    
    ![rs-dev-workshop-offline-news-inverted-list-build](/images/offline-codebuild-inverted-list.png)
    
