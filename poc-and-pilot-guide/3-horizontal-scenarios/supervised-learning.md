# Supervised learning

The supervised learning approach groups those Machine Learning algorithms that expect to get both the inputs and the corresponding outputs in the training process. The term *supervised* comes from the fact that, providing the expected outputs, we are *guiding* the algorithm towards learning how to map inputs to more or less correct outputs.

In its simplest form, the input data provided during the training process is a matrix where each row corresponds to an input entity (also commonly referred as a case) and each column to one property of the entity. The expected outputs are usually provided as a vector, each element of the vector corresponding to one entity. The training process aims to learn a function that transforms inputs into outputs, the goal being to be as successful as possible when data other than the training data is provided as an input. This function is also called an *objective function*.

Classification, regression, and feature (or representation) learning are examples of fundamental supervised learning approaches. Other approaches like similarity learning and anomaly detection are derived from them. They are popular and specific enough to be mentioned as individual approaches as well.

Combinations of multiple models as opposed to using single models are commonly referred as ensemble models. Ensemble models approaches are available for both classification and regression. 

## Classification

A classification problem occurs when the expected outputs are categorical (discrete). When there are only two categories the problem is also referred as binary classification. 

Some of the most common types of cases to be addressed are:

Name | Description
--- | ---
Classification on tabular data | The data is available in the form of rows and columns, potentially originating from a wide variety of data sources.
Classification on image/sound data | The subject of classification are images/sounds. Training data consists of images/sounds whose categories are already known. Several steps need to be performed during the preparation phase to transform images/sounds into numerical vectors accepted by the algorithms.
Classification on text data | The subject of classification is text. Training data consists of texts whose categories are already known. Several steps need to be performed during the preparation phase to transform text into numerical vectors accepted by the algorithms.

Examples of classification problems include:
- Computer vision (tracking, medical imaging, character recognition etc...)
- Speech recognition
- Biometric identification
- Document classification 
- Natural language processing
- Credit scoring in banking
- Anomaly detection
- Recommender systems

Some of the most widely used classification machine learning algorithms are:

- [Logistic Regression](https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression) (linear classifier)
- [Naive Bayes](https://scikit-learn.org/stable/modules/naive_bayes.html#bernoulli-naive-bayes) (linear classifier)
- [Perceptron](https://docs.microsoft.com/en-us/python/api/nimbusml/nimbusml.linear_model.averagedperceptronbinaryclassifier?view=nimbusml-py-latest) (linear classifier)
- [Light Gradient Boosting Machines](https://lightgbm.readthedocs.io/en/latest/index.html)
- [Gradient Boosting](https://scikit-learn.org/stable/modules/ensemble.html#classification)
- [K-Nearest Neighbors](https://scikit-learn.org/stable/modules/neighbors.html#nearest-neighbors-regression)
- [Support Vector Machines](https://docs.microsoft.com/en-us/python/api/nimbusml/nimbusml.linear_model.linearsvmbinaryclassifier?view=nimbusml-py-latest)
- [Decision Trees](https://scikit-learn.org/stable/modules/tree.html#decision-trees)
- [Linear Support Vector Classification (SVC)](https://scikit-learn.org/stable/modules/svm.html#classification)
- [Support Vector Classification (SVC)](https://scikit-learn.org/stable/modules/svm.html#classification)
- [Random Forests](https://scikit-learn.org/stable/modules/ensemble.html#random-forests)
- [Extremely Randomized Trees](https://scikit-learn.org/stable/modules/ensemble.html#extremely-randomized-trees)
- [Xgboost](https://xgboost.readthedocs.io/en/latest/parameter.html)
- [Deep Neural Network (DNN) Classifier](https://www.tensorflow.org/api_docs/python/tf/estimator/DNNClassifier)
- [Deep Neural Network (DNN) Linear Classifier](https://www.tensorflow.org/api_docs/python/tf/estimator/LinearClassifier)
- [Stochastic Gradient Descent (SGD)](https://scikit-learn.org/stable/modules/sgd.html#sgd)

## Regression

A regression problem occurs when the expected outputs are numerical (continuous).

Some of the most common types of cases to be addressed are:

Name | Description
---  | ---
Regression on tabular data | The data is available in the form of rows and columns, potentially originating from a wide variety of data sources.
Regression on image/sound data | The subject of classification are images/sounds. Training data consists of images/sounds whose numerical scores are already known. Several steps need to be performed during the preparation phase to transform images/sounds into numerical vectors accepted by the algorithms.
Regression on text data| The subject of classification is text. Training data consists of texts whose numerical scores are already known. Several steps need to be performed during the preparation phase to transform text into numerical vectors accepted by the algorithms.

Examples of regression problems include:
- Predict housing prices
- Customer churn
- Customer Lifetime Value prediction
- Forecasting (time series)
- Anomaly detection
- Time series forecasting

Some of the most widely used regression machine learning algorithms are:

- [Elastic Net](https://scikit-learn.org/stable/modules/linear_model.html#elastic-net)
- [Light Gradient Boosting Machines](https://lightgbm.readthedocs.io/en/latest/index.html)
- [Gradient Boosting](https://scikit-learn.org/stable/modules/ensemble.html#classification)
- [K-Nearest Neighbors](https://scikit-learn.org/stable/modules/neighbors.html#nearest-neighbors-regression)
- [Decision Trees](https://scikit-learn.org/stable/modules/tree.html#decision-trees)
- [LARS Lasso](https://scikit-learn.org/stable/modules/linear_model.html#lars-lasso)
- [Stochastic Gradient Descent (SGD)](https://scikit-learn.org/stable/modules/sgd.html#regression)
- [Random Forests](https://scikit-learn.org/stable/modules/ensemble.html#random-forests)
- [Extremely Randomized Trees](https://scikit-learn.org/stable/modules/ensemble.html#extremely-randomized-trees)
- [Xgboost](https://xgboost.readthedocs.io/en/latest/parameter.html)
- [Deep Neural Network (DNN) Regressor](https://www.tensorflow.org/api_docs/python/tf/estimator/DNNRegressor)
- [Linear Regressor](https://www.tensorflow.org/api_docs/python/tf/estimator/LinearRegressor)
- [Fast Linear Regressor](https://docs.microsoft.com/en-us/python/api/nimbusml/nimbusml.linear_model.fastlinearregressor?view=nimbusml-py-latest)
- [Online Gradient Descent Regressor](https://docs.microsoft.com/en-us/python/api/nimbusml/nimbusml.linear_model.onlinegradientdescentregressor?view=nimbusml-py-latest)

In the case of time series forecasting, the following algorithms are also used:
- [Auto-ARIMA](https://www.alkaline-ml.com/pmdarima/modules/generated/pmdarima.arima.auto_arima.html#pmdarima.arima.auto_arima)
- [Prophet](https://facebook.github.io/prophet/docs/quick_start.html)
- Forecast Temporal Convolutional Network (TCN)


## Feature (representation) learning

Feature engineering is one of the core techniques that can be used to increase the chances of success in solving machine learning problems. Having the right input features is a critical prerequisite for training high-quality models. Feature (or representation) learning is used to transform sets of inputs into other inputs that are potentially more useful in solving a given problem. An example of such a problem occurs in data sets that have multiple categorical features with high cardinality. Another example is the problem of classifying images where the original form of the data is not suited for tasks like classification for instance.

The supervised approach of feature learning is based on learning the new features using data that has already been labeled.

## Similarity learning

The problem of identifying similarity is closely related to classification and regression with the difference that the objective function measures the degree of similarity between two entities. Similarity learning is quite often used in recommendation systems as well in solving verification problems (speech, face, and the like).

Similarity learning can be approached as a classification problem, case in which the similarity function maps pairs of entities to a finite number of similarity levels (ranging from 0/1 to any number of levels).

Similarity learning can be also approached as a regression problem, case in which the similarity function maps pairs of entities to numerical values. A variation of this approach where the supervision form is weakened from an exact measure to an ordering measure is known as ranking similarity learning. This approach is a better fit for real-life large-scale problems.

As with classification or regression, similarity learning can be applied on tabular, image/sound, or text data.

## Anomaly detection

The supervised approach of anomaly detection is fundamentally a binary classification problem where entities must be classified ar either *normal* or *anomaly*. What makes anomaly (or outlier) detection such a special case is the ratio between the two classes. The number of entities in the *anomaly* class is several orders of magnitude smaller than that of entities in the *normal* class. That makes training high-quality models more difficult than in most other cases of classification.

The supervised approach of anomaly detection is based on using a training data set that has already been labeled as normal/anomaly.

## Ensemble models

The most popular ensemble models approaches are:
- Voting - calculates a weighted average of predicted class probabilities (for classification) or predicted regression targets (for regression)
- Stacking - trains a meta-model based on the output of individual models. Examples of stacking meta-models include LogisticRegression (for classification) and ElasticNet (for regression/forecasting)

[The ensemble models approach in Azure Machine Learning service](https://docs.microsoft.com/bs-latn-ba/azure/machine-learning/service/concept-automated-ml#ensemble) is based on the [Caruana selection algorithm](http://www.niculescu-mizil.org/papers/shotgun.icml04.revised.rev2.pdf).