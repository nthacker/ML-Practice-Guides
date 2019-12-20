# Maintainability and extensiblity

The following aspects should be considered when addressing the maintainability and extensiblity of your machine learning solution:

- Split your workloads into manageable components using [ML pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines)
- Use a combination of Azure Machine Learning service and Azure DevOps features to [create end-to-end, transparent and manageable MLOps processes](https://docs.microsoft.com/en-us/azure/devops/pipelines/targets/azure-machine-learning)
- [Collecting data for production models](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-access-data)
- [Monitoring and collecting data for web service endpoints](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-enable-app-insights)
- Monitoring Azure Machine Learning service metrics with [Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-platform-metrics) - the metrics of interest are the ones from the ```Machine Learning Service``` Azure Monitor namespace
- Periodically inspecting the Azure Machine Learning service activity log

## Creating building blocks with ML pipelines

Use of Azure Machine Learning service pipelines yields the following [benefits](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines?view=azure-devops#key-advantages):

- Simplicity
- Speed
- Repeatability
- Flexibility
- Versioning and tracking
- Modularity
- Quality assurance
- Cost control

Your ML pipelines should focus on workloads like:

- Data preparation
- Training and scoring configuration
- Training and validation
- Deployment

Make sure you have a good understanding of [the steps involved](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines?view=azure-devops#coordinating-the-steps-involved) in creating and running a ML pipeline.


