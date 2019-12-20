# Overview of platforms, services, and tools

## Platforms

### Microsoft Azure

[Microsoft Azure](https://azure.microsoft.com) is the platform providing a comprehensive set of services needed to deliver a successful machine learning PoC/Pilot project. 


## Services
  
### Azure Machine Learning service

[Azure Machine Learning service](https://azure.microsoft.com/en-us/services/machine-learning-service/) is a Microsoft Azure service for building, training, and deploying machine learning models. It enables you to use the tools and frameworks of your choice and increase productivity using components like automated machine learning. 

The service provides support for managing the core assets involved in machine learning projects:

Name | Description
--- | ---
Datasets | Define, version, and monitor datasets used in machine learning runs.
Experiments / Runs | Organize machine learning workloads and keep track of each task executed through the service.
Pipelines | Structured flows of tasks to model complex machine learning flows.
Models | Model registry with support for versioning and deployment to production.
Endpoints | Expose real-time endpoints for scoring as well as pipelines for advanced automation.

The service also provides support for managing the resources needed to run machine learning tasks:

Name | Description
--- | ---
Compute | Manage compute resources used by machine learning tasks.
Environments | Templates for standardized environments used to create compute resources.
Datastores | Data sources connected to the service environment (e.g. blob stores, file shares, Data Lake stores, SQL databases).

The service provides the following categories of compute resources:

Name | Description
--- | ---
Training clusters | Machine Learning service compute VM clusters used to run training tasks.
Inference clusters | [Azure Kubernetes Service](https://azure.microsoft.com/en-in/services/kubernetes-service/) clusters used to deploy trained machine learning models.
Attached compute | External compute resources used by the service (e.g. VM, [Azure Databricks](https://azure.microsoft.com/en-us/services/databricks/) cluster, [Data Lake Analytics](https://azure.microsoft.com/en-us/services/data-lake-analytics) compute, [HDInsight](https://azure.microsoft.com/en-us/services/hdinsight/) cluster). 
Notebook VMs | VMs used to run machine learning notebooks.

The service provides the following features to author machine learning tasks:

Name | Description
--- | --- 
Automated ML | Automate the process of exploring multiple approaches to solve problems based on combinations of algorithms and hyperparameter values.
Visual Interface | Interactive UI for the development of machine learning workloads.
Notebooks | Notebook experience for exploring and authoring machine learning workloads.


### Azure Notebooks

[Azure Notebooks](https://notebooks.azure.com/) enables you to develop and run code from anywhere with Jupyter notebooks on Azure. 

### Azure Databricks

[Azure Databricks](https://azure.microsoft.com/en-us/services/databricks/) enables you to unlock insights from all your data and implement data processing and machine learning workloads, set up Apache Spark environments, autoscale, and collaborate on shared projects in an interactive workspace. Azure Databricks supports Python, Scala, R, Java, and SQL, as well as data science frameworks and libraries including TensorFlow, PyTorch, and scikit-learn.

### Azure DevOps

[Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) enables you to manage all aspects of your machine learning projects using advanced features like boards, pipelines, repos, test plans and artifacts. Combined with features from the Azure Machine Learning service, Azure DevOps provides the core backbone of end-to-end, comprehensive MLOps implementations.


## Tools

### Azure Machine Learning service Python SDK

The Azure Machine Learning service exposes an API which can be consumed via the [Azure Machine Learning service Python SDK](https://docs.microsoft.com/en-us/python/api/overview/azure/ml/intro?view=azure-ml-py). The SDK can be used to manage the following key areas:

- Explore, prepare and manage the lifecycle of your datasets used in machine learning experiments.
- Manage cloud resources for monitoring, logging, and organizing your machine learning experiments.
- Train models either locally or by using cloud resources, including GPU-accelerated model training.
- Use automated machine learning, which accepts configuration parameters and training data. It automatically iterates through algorithms and hyperparameter settings to find the best model for running predictions.
- Deploy web services to convert your trained models into RESTful services that can be consumed in any application.

### Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) is a lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux. It comes with built-in support for JavaScript, TypeScript and Node.js and has a rich ecosystem of extensions for other languages (such as C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity).

The [Azure Machine Learning for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-ai) extension enables you to [use Azure Machine Learning](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-vscode-tools) from Visual Studio Code.

### Visual Studio

[Visual Studio](https://visualstudio.microsoft.com/) is Microsoft's core development environment that supports a wide range of workloads like web and cloud, Windows, mobile and gaming, Office and SharePoint, and Data Science and analytical applications.

Visual Studio's [support for Python](https://visualstudio.microsoft.com/vs/features/python/) enables direct integration with the Azure Machine Learning service via the Python SDK.

### Azure Portal

The [Azure Portal](https://portal.azure.com) provides support for interactive management and development of machine learning solutions. The following features are available:

Name | Description
--- | ---
Azure Machine Learning service workspace management | Create, configure, and manage Azure Machine Learning service workspaces.
[Azure Machine Learning service assets management portal](https://ml.azure.com) | New portal experience to manage Azure Machine Learning assets.
Automated ML user experience | Create and manage automated ML workloads.
Visual Interface | Visual designer to create and manage machine learning workloads.
Notebooks | Organize and browse interactive machine learning notebooks.

### Libraries

Azure Machine Learning service enables you to use a wide range of common machine learning libraries. Here are a few of the most widely used ones:

Name | Description
--- | ---
[Scikit-Learn](https://scikit-learn.org) | One of the most popular libraries for machine learning, built on NumPy, SciPy, and matplotlib.
[Tensorflow](https://www.tensorflow.org/) | Develop and train machine learning models based on deep learning approaches.
[Keras](https://keras.io/) | Keras is a high-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano.
[PyTorch](https://pytorch.org/) |Optimized tensor library for deep learning using GPUs and CPUs.
