---
title: Browse The Recommender System
weight: 42
---

## Explore the user experience
Copy the URL you just generate to the browser and you will see the following page:

![End-User-GUI](/images/end-user-gui.png)

You can input your name in the input field:

![Name-Input-Field](/images/name-input-field.png)

And click login icon.:

![Login-Icon](/images/login-icon.png)

Next time, you can input the same name to get recommendations based on the relating history. Optionally, you can just click the shortcut key to login the system. This will consider you as the new user each time:

![Look-Around](/images/look-around.png)

Suppose you login the system as the `gcr-rs-admin`. You will see the following page:

![Cold-Start](/images/cold-start.png)

You can tell that you are considered as the brand new user for this system at the right corner:

![Login-Time](/images/login-time.png)

Then you can see that the reading history and user portrait are empty:

![Empty-History-Portrait](/images/empty-history-portrait.png)

Since you are the new user, you get the recommendation list generated from the **cold start logic**. In the cold start logic, different types of news are randomly sampled:

![Cold-Start-News](/images/cold-start-news.png)

Actually, you can navigate different types of news and pick up what you like. The reading history and user portrait will change accordingly:

![Different-Types-News](/images/dtn.png)

After clicking at three pieces of news, you will see the recommendation list in the first channel. The recommendation result consists of two parts. The first 
part is top recommendation according to the most interested type in your portrait. In this example, it seems that **gcr-rs-admin** is very interested in
the entertainment, the first 2-3 lines of recommendation list are entertainment news:

![Top-Type-News](/images/top-type-news.png)

The second part is generated from the similar contents of what you clicked. If you click 'recommend' again, you will get another recommendation list:

![Recommend-type-1](/images/recommend-type-1.png)

You will also notice that there are scores for the type of news you may like:

![User-Portrait](/images/user-portrait.png)

If you navigate the recommendation list, you will notice some results with disparity tag. This means the system will push some types of news that you never read to discover the possible interests:

![Disparity](/images/disparity.png)

Now, you know almost everything about this demo. Please feel free to have a try!

## How to generate recommendation list (optional)

If you have interests in understanding more about the knowledge behind this engine, you can check the following content. 

If it is the first time that you login, the recommendation list will come from cold start logic. And each time you click the news, the user portrait will update.

If you click news at least 3 times, the recommendation list will come from the a sequence of logic, from recall to filter:

![Application Logic](/images/application-logic.png)

In real recommender system, it is not a good idea to apply complex models to all the items. We need some efficient methods to find promising candidates for the
current user. This is what the recall(retrieve) stage should do. For instance, the recall logic can find top 1,000 items from the whole 1,000,000. Then, we use
complex algorithms to rank these 1,000 items and find top 100 ones. Before pushing to the end user, we may add some custom logic to these ranked items, like disparity logic. This stage is called filter logic:

![Recall-Rank-Filter](/images/recall-rank-filter.png)

This is the 4-way recall logic, including news type, news keywords, news entity embedding learned from knowledge graph and user portrait. The recall logic finds
the most promising candidates from these perspectives:

![Recall-Logic](/images/recall-logic.png)

The rank logic is the knowledge-graph based ranking algorithm (DKN). The click history of the current user is sent to the model. All the news are encoded using
knowledge graph and the model predicts whether the current user will click the alternative news:

![Rank-Logic](/images/rank-logic.png)






