# Unsupervised learning

The unsupervised learning approach groups those Machine Learning algorithms that rely only on inputs in the training process. The term *unsupervised* comes from the fact that, not having the the expected outputs, the algorithm attempts to find on its own hidden structures in the data.

In its simplest form, the input data provided during the training process is a matrix where each row corresponds to an input entity (also commonly referred as a case) and each column to one property of the entity. Unlike in supervised learning, no expected outputs are provided. The training process aims to identify common aspects between entities and then use the presence or absence of these to produce various results.

Clustering is an example of a fundamental unsupervised learning approaches. Other approaches like feature (or representation) learning and anomaly detection are popular and specific enough to be mentioned as individual unsupervised approaches as well.

## Clustering

A clustering problem occurs when entities from the input data set must be assigned into a finite number of subsets (commonly referred as clusters) while maximizing intra-cluster similarity and inter-cluster dissimilarity. The level of similarity is assessed using various measures that yield a measurement of each cluster's compactness as well as the separation between clusters.

In most cases, the number of clusters is not defined a priori. Multiple attempts (using different numbers of clusters) are made and the chosen one is the one that yields the highest-quality clusters (both compact and well separated).

Clustering can be applied to tabular data, image/sound data, or text data. For the last two categories (image/sound and text) data must be transformed during the pre-processing phase into a format accepted by clustering algorithms (which is usually a numerical tabular one).

## Feature (representation) learning

Feature engineering is one of the core techniques that can be used to increase the chances of success in solving machine learning problems. Having the right input features is a critical prerequisite for training high-quality models. Feature (or representation) learning is used to transform sets of inputs into other inputs that are potentially more useful in solving a given problem. An example of such a problem occurs in data sets that have multiple categorical features with high cardinality. Another example is the problem of classifying images where the original form of the data is not suited for tasks like classification for instance.

The unsupervised approach of feature learning is based on learning the new features without having labeled input data. Clustering is also considered a form of feature learning since the cluster identifier is actually a new feature generated for each entity in the data set.

Other types of algorithms used in unsupervised feature learning include:
- Principal component analysis (PCA) which more a statistical approach than a Machine Learning approach (and thus used more in exploratory data analysis)
- Independent component analysis
- Autoencoder (deep learning)
- Matrix factorization

One interesting aspect of using neural nets (and especially deep neural nets) in feature learning is that they actually produce hierarchies of features with lower-level ones aggregated into more and more abstract ones.

# Anomaly detection

The unsupervised approach of anomaly detection is fundamentally problem of identifying two major groups (clusters) of entities - the *normal* ones and the *abnormal* ones (the anomalies). What makes anomaly (or outlier) detection such a special case is the ratio between the two classes. The number of entities in the *anomaly* class is several orders of magnitude smaller than that of entities in the *normal* class. That makes training high-quality models more difficult than in most other cases of classification.

The unsupervised approach of anomaly detection is based on using a training data set that has no normal/anomaly labels available. It works under the above mentioned assumption regarding the ration between normal and abnormal entities and tries to identify the latter ones.