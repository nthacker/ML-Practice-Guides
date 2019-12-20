# Security and explainability

## Security

The complexity of machine learning projects generates security challenges that span the entire scope of training and scoring workloads. 

The following are typical security challenges for machine learning workloads:

Name | Description
--- | ---
Store training data | Ensure training data is stored with appropriate security.
Load training data | Ensure proper security is applied when connecting and reading from various data sources.
Prepare data | Ensure various intermediate forms and/or formats of data used in data preparation processes are stored securely (even if storage is temporary).
Manage datastores | In general, ensure access to various datastores is performed in a secure way. Avoid spreading datastore connecting credentials is source code, notebooks, config files, and the like. The recommended approach for Azure Machine Learning service is to use the [register datastore](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-access-data) capabilities for secure management of connections. Also, make sure you understand the [data encryption features of Azure Machine Learning service](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-enterprise-security#data-encryption).
Manage trained models | Ensure trained machine learning models are stored in a secure environment (e.g. the Azure Machine Learning service model registry with versioning). Ensure trained models are not save (and left there) in various compute environments used for training workloads.
Deploy models for real-time scoring | Ensure models are deployed in secure environments. Ensure web service endpoints exposed for real-time scoring are properly secured and monitored for attempts to breach security (e.g. by using [HTTPS](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-secure-web-service), [security keys vs. tokens](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-enterprise-security#authentication-for-web-service-deployment), Azure AD integration etc...). Make sure you follow proper security guidelines for [ACI](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-image-security) or [AKS](https://docs.microsoft.com/en-in/azure/aks/concepts-security).
Deploy models for batch scoring | Ensure models are deployed in secure environments. Ensure proper security of all actions capable of starting a batch processing job.
Manage secrets | Ensure secrets are not left in easily accessible places (source code files, source code repositories, notebooks, scripts etc...). Wherever possible, use approaches that do not require specifying credentials at run-time. Perform the task of [regenerating storage account keys](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-change-storage-access-key) ar regular intervals of time.
Manage workspaces | The Azure Machine Learning service is the main security boundary for [controlling access to machine learning resources](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-enterprise-security#authorization). Make sure you understand the [security impact of an Azure machine learning workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-enterprise-security#securing-compute-targets-and-data).
Manage networking | Secure AML training and scoring jobs using [virtual networks](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-enable-virtual-network).


In addition to securing environments and assets, it is equally important to constantly monitor models deployed in production environments for potential security flaws and/or attacks. The following aspects should be taken into consideration:

- [Collecting data for production models](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-access-data)
- [Monitoring and collecting data for web service endpoints](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-enable-app-insights)
- Monitoring Azure Machine Learning service metrics with [Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-platform-metrics) - the metrics of interest are the ones from the ```Machine Learning Service``` Azure Monitor namespace
- Periodically inspecting the Azure Machine Learning service activity log

## Explainability

In most PoC/Pilot machine learning projects, the ability to easily explain the end-to-end process is one of the key requirements. This addresses one of the top customer concerns - the fear to fail in understanding the inner workings of the solution at various levels of detail.

Explainability in machine learning projects involves two core aspects:

- The transparency of the processes (e.g. training, scoring, selecting models, etc...)
- The interpretability of trained machine learning models

For process transparency, the following aspects should be considered:

- Split your workloads into manageable components using [ML pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines)
- Use a combination of Azure Machine Learning service and Azure DevOps features to [create end-to-end, transparent and manageable MLOps processes](https://docs.microsoft.com/en-us/azure/devops/pipelines/targets/azure-machine-learning)
- Focus on logging and data collection to trace everything that happens inside your custom code

For model interpretability, the following aspects should be considered:

- Use the Azure Machine Learning service [model interpretability features](https://docs.microsoft.com/en-us/azure/machine-learning/service/machine-learning-interpretability-explainability) based on explainers and visual representations
- Consider using the [Open Neural Network Exchange Format (ONNX)](https://onnx.ai/) to [standardize and accelerate](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-onnx) your machine learning models
