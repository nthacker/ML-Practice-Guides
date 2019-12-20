# Model training and evaluation

Training, evaluating, and selecting the right Machine Learning models is at the core of each modern data science process. These processes are not possible though without another critical step: the correct preparation of data. Correctly prepared data implies the following:

- Thorough understanding of the data - typically gained via a mix of business process knowledge and exploration.
- High quality of data - resulting from a combination of processes like cleaning, missing values handling, outlier detection, and transformation.
- Enrichment at feature level - a process which results in new features being derived from the original features available in the data set(s). In most cases, enrichment is followed by a feature selection process aimed towards reducing the dimensionality of the training problem. Complementary to feature selection, dimensionality reduction algorithms can also be used to achieve this goal.

The training of a Machine Learning model is the process through which a mathematical model is built from data that contains both inputs and expected outcomes (or only inputs in the case of unsupervised learning). There are several classes of algorithms available to build the model, like classification, regression, clustering, feature learning, and others.

The resulting trained model must always be validated to ensure the chosen algorithm has performed in a proper way on the data made available to it. One of the most widely used accuracy estimation techniques in the holdout method with splits data in a training part and a test part. The test part (which already has the correct “answers”) is used to calculate the value of the accuracy measure. Other widely used accuracy estimation techniques are K-fold-cross-validation and bootstrap. The process of calculating the accuracy of a model is commonly referred as Model Evaluation.

In most cases, there is no single obvious choice of an algorithm or even of a specific parameterization of an algorithm. The typical data science process will imply the training and the evaluation of several models and, within the context of each model’s algorithm, the use of multiple combinations of parameter values (commonly referred as hyperparameters). This will result in multiple trained models, each with its own evaluation results. The process of selecting the best model(s) is commonly referred as Model Selection.

## Model Training introduced

The training of a Machine Learning model is the process through which a mathematical model is built from data that contains both inputs and expected outcomes (or only inputs in the case of unsupervised learning). There are several classes of algorithms available to build the model, like classification, regression, clustering, feature learning, and others.

Azure Machine Learning service provides a comprehensive environment to implement data science processes, giving you a centralized place to work with all the artifacts involved in the process. The top level resource for an instance of the Azure Machine Learning service is the workspace. The following diagram illustrates the high level taxonomy of the workspace:

![The high level taxonomy of the Azure Machine Learning workspace](media/azure-machine-learning-taxonomy.png)

The following table provides a brief description of all the elements from this taxonomy that are involved in the Model Training process.

| Name           | Description                                                                                                                                                                                                  |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Experiment     | A generic context for handling runs. Think about it a logical entity you can use to organize your Model Training processes.                                                                                  |
| Run            | A Model Training run used to build a trained model. Contains all artifacts associated with a training process, like output files, metrics, logs, and a snapshot of the directory that contains your scripts. |
| Estimator      | An Estimator is an alternative higher-level abstraction used to construct run configurations when training deep learning models.                                                                             |
| Compute target | Defines a compute resource used to either run a Model Training script or host a service deployment (associated with a trained Machine Learning model).                                                       |
| Model registry | Keeps track of all models in an Azure Machine Learning workspace. Models are either produced by a Run or originating from outside Azure Machine Learning (and made available via model registration).        |

The following diagram identifies the positions of these elements in the high level taxonomy of the Azure Machine Learning workspace:

![The positions of the elements involved in Model Training in the taxonomy of the Azure Machine Learning workspace](media/azure-machine-learning-taxonomy-marked.png)

## Model Evaluation introduced

The evaluation of a Machine Learning model is the process through which a set of performance metrics are calculated for an already trained model in order to assess its performance. While these performance metrics play an important role in understanding the performance on the model they were calculated for, they are also critical in the model selection process - a process through which the best model is selected from a number of candidate trained models.

Azure Machine Learning service provides a comprehensive environment to implement Model Evaluation, giving you a centralized place to store and access all model performance data. The collection of performance data can be either performed manually (through the training script itself using the [Azure Machine Learning SDK for Python](https://docs.microsoft.com/python/api/overview/azure/ml/install?view=azure-ml-py)) or automatically in the the case of automated training. There are multiple types of data that can be used to store performance data. Examples include numeric and string scalars, lists, tables, images, and custom files.

Model performance data can be programmatically accessed through the SDK and the Azure Portal can be used to view the raw version of it as well as various graphical representations (like confusion matrices, gain and lift charts, receiver operating characteristics curves, calibration plots, predicted vs. true charts, and histograms of residuals, to name just a few). In addition to the Azure Portal, third party tools like [MLFlow](https://mlflow.org/) and [TensorBoard](https://www.tensorflow.org/tensorboard/) can be integrated.