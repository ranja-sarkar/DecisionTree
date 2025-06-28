# Decision Trees

A **decision tree** consists of a series of sequential decisions (decision nodes) on features from a dataset. The resulting flow-like structure is navigated via conditional control statements or if-then rules, which split each node into two or more leaf nodes. 

To train a decision tree out of a dataset means to figure out the order in which the decisions should be assembled from the root to the leaves. New datapoint may then be passed from top down until the leaf (terminal) node is reached, representing a prediction for that datapoint. 

# Mutual Information

In **information theory**, the mutual information between two quantities is a measure of the extent to which knowledge of one quantity reduces uncertainty about the other. It quantifies the amount of information obtained about one random variable by observing another random variable. This concept is intimately linked to that of entropy of a random variable. It’s noteworthy that Shannon entropy (node-splitting criterion) is equivalent to minimizing the log loss (also called cross-entropy). 

Decision trees trained using entropy or Gini are comparable, and only in a few cases do results differ considerably. In the case of imbalanced data, entropy might be more prudent, yet Gini might train faster as it does not make use of logarithms.

See: https://en.wikipedia.org/wiki/Entropy_(information_theory)

Also see: https://scikit-learn.org/stable/modules/tree.html#shannon-entropy

-----

<img width="434" alt="dt" src="https://github.com/user-attachments/assets/30e02fdc-3420-47e1-9a28-669867a83ca6" />

Decision trees classify a dataset based on the features in the dataset. 

Information gain is a measure of the information a feature provides about a class. It is the metric to quantify the reduction in randomness of dataset, post-split into homogeneous subsets of data. The impurity of a dataset is measured using criterion like 𝒆𝒏𝒕𝒓𝒐𝒑𝒚 (H) and 𝑮𝒊𝒏𝒊 index.

<img width="260" alt="ig" src="https://github.com/user-attachments/assets/5cd97a94-50e6-474f-a9ed-b70f4049b128" />

In decision trees, each internal/decision mode represents a feature/attribute, each branch is a decision rule and each leaf node is the outcome/result. Decision node represents a parent class and leaf node represents a child class. The feature values at the child nodes are as pure as possible, and most informative about the target (response variable) in the dataset. A node with only one class is considered pure. 

<img width="353" alt="dn" src="https://github.com/user-attachments/assets/656a8b20-bf59-4e21-a40a-9c3dd0464c90" />

Pure samples have zero entropy, meaning there is no uncertainty in the outcome (from a collection of labeled datapoints). Impure samples (dissimilar datapoints) have larger entropy values.

Higher impurities indicate a mix (heterogeneity) of different classes within the dataset. Each node has an entropy value. The parent node entropy is larger than the average entropy of 2 child nodes and the node splitting continues (entropy reduces) until a predefined stopping criterion is met. 

Read: https://sebastianraschka.com/faq/docs/decisiontree-error-vs-entropy.html

The recursive process stops if after a split all elements in a child node are of the similar. Additional stopping conditions may be imposed, such as requiring a minimum number of samples per leaf to continue splitting, or finishing when the trained tree has reached a given maximum depth. 

https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html


High **information gain (IG)** implies that a split leads to more homogenous subsets, making it favorable for building an accurate classifier. A decision tree algorithm uses information gain to split a node and choose the features that lead to maximum reduction in uncertainty (impurity) in the child nodes over that in the parent node. 

<img width="222" alt="11" src="https://github.com/user-attachments/assets/3163e8df-d86a-42b2-bc46-e6216ef0c3e9" />

For a number of classes, p_k is the fraction of items labeled with a class k. Gini index (G) is faster given its numerical form, it is less computationally intensive and measures the degree or probability of wrong classification when a feature is randomly chosen. The goal is to find the feature and threshold that best splits the dataset into subsets with lower impurities. 

<img width="392" alt="22" src="https://github.com/user-attachments/assets/79ade31e-d799-4b4b-9386-226e4a527f4f" />


-------

Decision Trees are simple models that are easy to interpret. They're fast to train and require minimal data preprocessing. And they handle outliers with ease. Yet they suffer from a major limitation, and that is their instability compared with other predictors. They can be extremely sensitive to small perturbations in the data: a minor change in the training example can result in a drastic change in the structure of the tree. 


**Isolation Forest is one algorithm for anomaly detection in data.** It's an unsupervised learning (unlabeled training data) algorithm that assumes most inflowing data are normal and only a minor percentage is anomalous. 

In Isolation Forest, randomly sub-sampled data is processed based on randomly selected features. The samples that travel deeper into the tree are less likely to be outliers as they require more cuts to isolate.

<img width="316" alt="33" src="https://github.com/user-attachments/assets/009b5e4b-7824-48b3-a3d8-65baf8e888b2" />

---------

Decision Trees are subject to high variance when exposed to small perturbations of the training data. They typically lead to overfitting (unable to distinguish between persistent and random patterns in data). This is problematic because it means that our model won't perform well when exposed to new data. 


There are ways to prevent excessive growth of Decision Trees by pruning them, for instance constraining their maximum depth, limiting the number of leaves that can be created, or setting a minimum size of samples in each leaf and not allowing leaves with too few items in them.

What about the issue of high variance? 

Well, unfortunately it's an intrinsic characteristic when training a single Decision Tree.


One way to alleviate the instability induced by perturbations is to introduce an extra layer of randomness in the training process. In practice this can be achieved by creating collections of Decision Trees trained on slightly different versions of the dataset, the combined predictions of which do not suffer so heavily from high variance. This approach opens the door to one of the most successful ML algorithms thus far - random forest.


   
   
