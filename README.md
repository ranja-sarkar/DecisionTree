# Tree-based models

A decision tree consists of a series of sequential decision nodes on features from a dataset. The resulting flow-like structure is navigated via conditional control statements or if-then rules. The rules split each node into two or more leaf nodes. To train a decision tree out of a dataset means to figure out the order in which the decisions should be assembled from the root to the leaves. New datapoint may then be passed from top down until the leaf or terminal node is reached, representing a prediction for that datapoint. 

<img width="410" height="208" alt="dt1" src="https://github.com/user-attachments/assets/b7dcd752-5059-453a-a19c-327f78176c27" />

Decision trees classify a dataset based on the features in the dataset. In decision trees, each internal/decision mode represents a feature/attribute, each branch is a decision rule and each leaf node is the outcome/result. Decision node represents a parent class and leaf node represents a child class. The feature values at the child nodes are as pure as possible, and most informative about the target/response in the dataset. 

<img width="332" height="173" alt="dt" src="https://github.com/user-attachments/assets/0323ed37-1a74-42b7-bdbc-7d4a70818a67" />

Decision trees are simple models that are easy to interpret. They're fast to train and require minimal data pre-processing. And they handle outliers with ease. Yet they suffer from a major limitation, and that is their instability as compared to other predictors. They can be extremely sensitive to small perturbations in the data, that is a minor change in the training example can result in a drastic change in the structure of the tree. 

# Mutual Information

In information theory, the mutual information between two quantities is a measure of the extent to which knowledge of one quantity reduces uncertainty about the other. It quantifies the amount of information obtained about one random variable by observing another random variable. This concept is intimately linked to that of entropy of a random variable. 

The node-splitting criterion in a decision tree is [Shannon entropy](http://www.ueltschi.org/teaching/chapShannon.pdf), which is equivalent to minimizing the log loss (also called cross-entropy). 

Information gain is a measure of the information a feature provides about a class. It is the metric to quantify the reduction in randomness of dataset post-splitting, into homogeneous subsets of data. The impurity of a dataset is measured using criterion like 𝒆𝒏𝒕𝒓𝒐𝒑𝒚 (H) and 𝑮𝒊𝒏𝒊 (G) index. 

<img width="222" alt="11" src="https://github.com/user-attachments/assets/3163e8df-d86a-42b2-bc46-e6216ef0c3e9" />

Decision trees trained using entropy or Gini index are comparable, and only in a few cases do results differ considerably. In the case of imbalanced data, entropy might be more prudent, yet Gini index might train faster as it does not make use of logarithms. For a number of classes, p_k is the fraction of items labeled with a class k. Gini index/coefficient is faster given its numerical form, it is less computationally intensive and measures the degree or probability of wrong classification when a feature is randomly chosen. The goal is to find the feature and threshold that best splits the dataset into subsets with lower impurities.

<img width="392" alt="22" src="https://github.com/user-attachments/assets/79ade31e-d799-4b4b-9386-226e4a527f4f" />


High information gain (IG) implies that a split leads to more homogenous subsets, making it favorable for building an accurate classifier. 
A decision tree algorithm uses IG to split a node and choose the features, that lead to maximum reduction in uncertainty or impurity in the child nodes over that in the parent node. 

<img width="260" alt="ig" src="https://github.com/user-attachments/assets/5cd97a94-50e6-474f-a9ed-b70f4049b128" />

A node with only one class is considered pure. Pure samples have zero entropy, meaning there is no uncertainty in the outcome. Impure samples (dissimilar datapoints) have larger entropy values.

Higher impurities indicate a mix (heterogeneity) of different classes within the dataset. Each node has an entropy value. The parent node entropy is larger than the average entropy of 2 child nodes and the node splitting continues (entropy reduces) until a predefined [stopping criterion](https://sebastianraschka.com/faq/docs/decisiontree-error-vs-entropy.html) is met. 

The recursive process stops if after a split all elements in a child node are similar. Additional stopping conditions may be imposed, such as requiring a minimum number of samples per leaf to continue splitting, or finishing when the trained tree has reached a given maximum depth. 

There are ways to prevent excessive growth of [decision trees](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html) by pruning them, like

📌 min_samples_leaf -> setting a minimum size of samples in each leaf (not allowing leaf nodes with too few items in them)

📌 max_depth -> constraining the maximum depth (nodes are expanded until all leaf nodes are pure or they contain less than the minimum number of samples required to split a node

📌 min_samples_split -> minimum number of samples required to split a node (a split at any depth is only considered if there're min_samples_leaf training samples in each of the left and right branches

📌 max_leaf_nodes -> limiting the number of leaf nodes that can be created (best nodes are defined as relative reduction in impurity, if it's None, then unlimited number of leaf nodes are created).

# Anomaly detection with decision trees 

Isolation Forest is a tree-based algorithm for anomaly detection. It is an unsupervised learning algorithm that assumes most inflowing data are normal and only a minor percentage is anomalous. In Isolation Forest, randomly sub-sampled data is processed based on randomly selected features. The samples that travel deeper into the tree are less likely to be outliers as they require more cuts to isolate.

<img width="316" alt="33" src="https://github.com/user-attachments/assets/009b5e4b-7824-48b3-a3d8-65baf8e888b2" />

#  A decision tree tends to overfit on data

A decision tree is subjected to high variance when exposed to small perturbations of the training data. It typically leads to overfitting, that is the tree is unable to distinguish between persistent pattern and random pattern in data. This is problematic because it means that our model won't perform well when exposed to new data. 

Well, the high variance is an intrinsic characteristic when training a single decision tree. One way to alleviate the instability induced by perturbations is to introduce an extra layer of randomness in the training process. In practice, this can be achieved by creating collection of decision trees trained on slightly different versions of the dataset, the combined (averaged) prediction of which do not suffer heavily from high variance. This approach opens the door to one of the most successful machine learning algorithms thus far - random forest.

[Random forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) is one of the ensemble learning algorithms. Well-placed randomness can enhance a decision tree model. A bagging (bootstrapping followed by aggregating) ensemble is [random forest](https://mlu-explain.github.io/random-forest/).

# Random Forest uses decision trees, Gradient Boosting does the same

[Gradient boosting](https://ranja-sarkar.github.io/2026/01/10/ensemble-learning.html) is another ensemble learning algorithm. Random forest is built for stability, gradient boosting (e.g. XGBoost) is built for peak performance - only if you know when to tell it to stop. What do I mean by this?

Random Forest reduces error by voting - it smoothens things out. Boosting reduces error by correcting - it sharpens things up. 
The former is the safe baseline. It averages out the noise. The latter is more powerful, but it’s high-maintenance. If you do not use [early stopping or tune your learning rate](https://ranja-sarkar.github.io/2026/02/12/neural-network.html), boosting will chase every outlier until the model is useless in reality. 

<img width="756" height="292" alt="compare" src="https://github.com/user-attachments/assets/df1e1bc1-e51d-457f-bc28-d1e2cb7b7e68" />


This explains why you can add like a thousand trees to a random forest and it won’t overfit, but if you do that with XGBoost, the model usually falls apart.





