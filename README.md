# Decision Trees

A decision tree consists of a series of sequential decisions (decision nodes) on features from a dataset. The resulting flow-like structure is navigated via conditional control statements or if-then rules, which split each node into two or more leaf nodes or terminal nodes. To train a decision tree out of a dataset means to figure out the order in which the decisions should be assembled from the root to the leaves. New datapoint may then be passed from top down until the leaf/terminal node is reached, representing a prediction for that datapoint.

Information Theory: https://monoskop.org/images/2/2f/Shannon_Claude_E_1956_The_Bandwagon.pdf

In information theory, the mutual information between two quantities is a measure of the extent to which knowledge of one quantity reduces uncertainty about the other. It quantifies the amount of information obtained about one random variable by observing another random variable. This concept is intimately linked to that of entropy of a random variable. It’s noteworthy that Shannon entropy (node-splitting criterion) is equivalent to minimizing the log loss (also called cross-entropy). 

See: https://en.wikipedia.org/wiki/Entropy_(information_theory)

Also see: https://scikit-learn.org/stable/modules/tree.html#shannon-entropy

Decision trees classify dataset into classes based on their features. Information gain is a measure of the information a feature provides about a class. 

<img width="434" alt="dt" src="https://github.com/user-attachments/assets/30e02fdc-3420-47e1-9a28-669867a83ca6" />
