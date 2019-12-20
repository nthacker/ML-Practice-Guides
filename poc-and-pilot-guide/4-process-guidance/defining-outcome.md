# Defining the outcome of PoC/Pilot (including packaging aspects)

As discussed previously, the outcome of a PoC is working code that validates or de-risks a narrowly scoped aspect of a machine learning project. A Pilot, on the other aims to provide a production-ready working solution that is gradually rolled out.

As the primary difference between a PoC and pilot is scope, the PoC and pilot each have a similar bill of materials (BoM) encapsulating what is delivered to the client at the conclusion of the project. The following tables summarize the delivered artifacts.

**Deliverables in a Proof of Concept or Pilot**

| Item | Includes |
| --- | --- |
| Git Repository | Application source code, unit and system tests, notebook artifacts, DevOps project artifacts, and documentation. |
| Jupyter notebooks | Notebooks implementing and documenting the approach taken for data prep, model training, model evaluation, model selection and model operationalization, including notebooks that use the AML SDK for the definition and execution of AML pipelines, execution and monitoring of training runs (on Notebook VM's, training clusters, or attached compute such as VM's, Azure Databricks, Data Lake Analytics or HDInsight), model registration and model deployment. |  
| DevOps project | Azure DevOps project containing build and release pipeline definitions and supporting automation scripts. |
| Visual Interface pipelines | Model development performed using the Azure Machine Learning Visual Interface results in pipelines that are created and stored within the Azure Machine Learning Workspace.
| Training data | Within Azure Machine Learning datasets are stored in flat file form within Azure Blobs or Azure Files. | 
| Model versions & experiment history | Within Azure Machine Learning, a history of all trained models is registered, associated with their annotations and performance characteristics. |
| Containers | Models used within predictive web services and scripts used for training each separately packaged as Docker Containers enabling repeatable deployment, stored within an Azure Container Registry instance. Environments describing the docker images, Python dependencies and Spark configuration registered within the Azure Machine Learning workspace. |
| Deployed predictive services | Within Azure Machine Learning, if models are operationalized as web services, these are often deployed to inference clusters running on the Azure Kubernetes Service. | 
| Documentation | Documentation may include the project charter, data dictionaries/summaries, system architecture diagrams, project management/planning documents, documents provided by the client, presentations and reports documenting the findings/conclusion of the PoC effort and setup instructions aiding reproducibility of the PoC. |
