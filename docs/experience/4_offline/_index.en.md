---
title: Action Model Update
weight: 44
---

If you click the system settings on the right, you will see three types of offline functions:

![Offline-Icon](/images/offline-icon.png)

As the recommender system runs, more and more action data is gathered in the system. It is a good practice to re-train your action model so that it can predict what user like more accurately. The parameters for training the model is already set for convenience in this workshop. If you click the icon for action model update, you will see the icon becomes gray:

![Action-Icon-Yellow](/images/action-icon-gray.png)


This means the step function behind is triggered.

{{% notice info %}}
This will take about 15 minutes to finish
{{% /notice %}}

When the training finishes this icon will become purple again:

![Action-Icon-Green](/images/action-icon-green.png)

If any error occurs, this icon will become red and you can click the link for this step function to see what happens:

![Action-Icon-URL](/images/action-icon-url.png)

When the model has already been trained, the offline logic will notice the online service to reload model. In this case, the rank service will be noticed to reload the trained model.

The other two offline functions will be introduced in the next page.


