# Anomaly_detection

## How to Execute ?
  The notebook can be downloaded and executed directly without any changes. The only which need to keep in mind is that the dataset and .ipynb files is present in same director and necessary libraries are installed.
  
## Why Isolation Forest Algorithm?
  Isolation Forests(IF), similar to Random Forests, are build based on decision trees. And since there are no pre-defined labels here, it is an unsupervised model. <h4>IsolationForests were built based on the fact that anomalies are the data points that are fewer in number and different from other.</h4>
  In an Isolation Forest, randomly sub-sampled data is processed in a tree structure based on randomly selected features. The samples that travel deeper into the tree are less likely to be anomalies as they required more cuts to isolate them. Similarly, the samples which end up in shorter branches indicate anomalies as it was easier for the tree to separate them from other observations.
  
  
  ## How do Isolation Forests work?
As mentioned earlier, Isolation Forests are nothing but an ensemble of binary decision trees. And each tree in an Isolation Forest is called an Isolation Tree(iTree). The algorithm starts with the training of the data, by generating Isolation Trees.

Let us look at the complete algorithm step by step:

- When given a dataset, a random sub-sample of the data is selected and assigned to a binary tree.
- Branching of the tree starts by selecting a random feature (from the set of all N features) first. And then branching is done on a random threshold ( any value in the range of minimum and maximum values of the selected feature).
- If the value of a data point is less than the selected threshold, it goes to the left branch else to the right. And thus a node is split into left and right branches.
- This process from step 2 is continued recursively till each data point is completely isolated or till max depth(if defined) is reached.
- The above steps are repeated to construct random binary trees.
- After an ensemble of iTrees(Isolation Forest) is created, model training is complete. During scoring, a data point is traversed through all the trees which were trained earlier. 
- Now, an ‘anomaly score’ is assigned to each of the data points based on the depth of the tree required to arrive at that point. This score is an aggregation of the depth obtained from each of the iTrees. 
- An anomaly score of -1 is assigned to anomalies and 1 to normal points based on the contamination(percentage of anomalies present in the data) parameter provided.


# Precision & Recall
![image](https://user-images.githubusercontent.com/22805226/170884283-435c673b-5dbe-42fe-9464-1ff3720fc8b6.png)

![image](https://user-images.githubusercontent.com/22805226/170884297-1b646979-21c3-49ba-9be6-e07408934879.png)

![image](https://user-images.githubusercontent.com/22805226/170884334-1ec2fb48-b137-442a-86a4-23caf565584a.png)

