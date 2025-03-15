# Decision Trees

A decision tree consists of a series of sequential decisions (decision nodes) on features from a dataset. The resulting flow-like structure is navigated via conditional control statements or if-then rules, which split each node into two or more leaf nodes or terminal nodes. To train a decision tree out of a dataset means to figure out the order in which the decisions should be assembled from the root to the leaves. New datapoint may then be passed from top down until the leaf/terminal node is reached, representing a prediction for that datapoint.

Information Theory: https://monoskop.org/images/2/2f/Shannon_Claude_E_1956_The_Bandwagon.pdf

In information theory, the mutual information between two quantities is a measure of the extent to which knowledge of one quantity reduces uncertainty about the other. It quantifies the amount of information obtained about one random variable by observing another random variable. This concept is intimately linked to that of entropy of a random variable. It’s noteworthy that Shannon entropy (node-splitting criterion) is equivalent to minimizing the log loss (also called cross-entropy). 

See: https://en.wikipedia.org/wiki/Entropy_(information_theory)

Also see: https://scikit-learn.org/stable/modules/tree.html#shannon-entropy

Decision trees classify dataset into classes based on their features. Information gain is a measure of the information a feature provides about a class. It is the metric to quantify the reduction in randomness of dataset, post-split into homogeneous subsets of data. 

<img width="434" alt="dt" src="https://github.com/user-attachments/assets/30e02fdc-3420-47e1-9a28-669867a83ca6" />

In decision trees, each internal/decision mode represents a feature/attribute, each branch is a decision rule and each leaf node is the outcome/result. Decision node represents a parent class and leaf node represents a child class. The feature values at the child nodes are as pure as possible, and most informative about the target (response variable) in the dataset. A node with only one class is considered pure. 

<img width="353" alt="dn" src="https://github.com/user-attachments/assets/656a8b20-bf59-4e21-a40a-9c3dd0464c90" />

The impurity of a dataset is measured using criterion like 𝒆𝒏𝒕𝒓𝒐𝒑𝒚 and 𝑮𝒊𝒏𝒊 index. Higher impurities indicate a mix (heterogeneity) of different classes within the dataset. Each node has an entropy value. The parent node entropy is larger than the average entropy of 2 child nodes and the node splitting continues (entropy reduces) until a predefined stopping criterion is met. 

Read: https://sebastianraschka.com/faq/docs/decisiontree-error-vs-entropy.html

High information gain (low information loss) implies that a split leads to more homogenous subsets, making it favorable for building an accurate classifier. A decision tree algorithm uses information gain to split a node and choose the features that lead to maximum reduction in uncertainty (impurity) in the child nodes over that in the parent node. 

<img width="222" alt="11" src="https://github.com/user-attachments/assets/3163e8df-d86a-42b2-bc46-e6216ef0c3e9" />

<img width="392" alt="22" src="https://github.com/user-attachments/assets/79ade31e-d799-4b4b-9386-226e4a527f4f" />

For a number of classes, p_k is the fraction of items labeled with a class k. Gini index (G) is faster given its numerical form, it is less computationally intensive and measures the degree or probability of wrong classification when a feature is randomly chosen. The goal is to find the feature and threshold that best splits the dataset into subsets with lower impurities. 

When dealing with imbalanced data, it becomes essential to choose only one criterion for evaluation of the model. The Gini index tends to be less sensitive to class imbalance, as it works to minimize the misclassification error which can be beneficial as it avoids overfitting to the majority class. 

https://mlu-explain.github.io/decision-tree/



-------

**Isolation Forest is one decision tree algorithm for anomaly detection in data.** 
It's an unsupervised learning (unlabeled training data) algorithm that assumes most inflowing data are normal and only a minor percentage is anomalous. 

In Isolation Forest, randomly sub-sampled data is processed based on randomly selected features. The samples that travel deeper into the tree are less likely to be outliers as they require more cuts to isolate.

<img width="316" alt="33" src="https://github.com/user-attachments/assets/009b5e4b-7824-48b3-a3d8-65baf8e888b2" />






