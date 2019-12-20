# Cost

The following table provides a detailed list of the most important cost generators in a machine learning project:

Category | Name | Description | Costs
--- | --- | --- | ---
Data ingestion and preparation | [Azure Data Factory](https://azure.microsoft.com/en-in/services/data-factory/) | Integrates various data silos, used to construct ETL and ELT processes using a serverless approach. | [Azure Data Factory pricing](https://azure.microsoft.com/en-in/pricing/details/data-factory/)
Data ingestion and preparation | [Azure Databricks](https://azure.microsoft.com/en-us/services/databricks/) | Highly scalable Apache Spark environment that supports Python, Scala, R, Java, and SQL, as well as data science frameworks and libraries including TensorFlow, PyTorch, and scikit-learn. Typically used when the data preparation workload is highly complex and resource intensive. | [Azure Databricks pricing](https://azure.microsoft.com/en-us/pricing/details/databricks/)
Data ingestion and preparation / Model training and evaluation / Batch scoring | AML compute | Compute resources managed via the Azure Machine Learning service workspace. | [AML compute pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machine-scale-sets/)
Model deployment (production) | [Azure Kubernetes Service](https://azure.microsoft.com/en-in/services/kubernetes-service/) | Fully managed service for deploying and managing containerised applications. | [AKS deployment pricing]( https://azure.microsoft.com/en-us/pricing/details/machine-learning-service/)
Model deployment (dev/test) | [Azure Container Instances](https://azure.microsoft.com/en-us/services/container-instances/) | Serverless containers environment.| [ACI deployment pricing](https://azure.microsoft.com/en-us/pricing/details/container-instances/)
Model deployment | [Azure Container Registry](https://azure.microsoft.com/en-us/services/container-registry/) | Private Docker container registry. AML service uses the Basic tier. | [ACR pricing](https://azure.microsoft.com/en-us/pricing/details/container-registry/)
All-purpose storage | [Azure Block Blob Storage](https://azure.microsoft.com/en-us/services/storage/blobs/) | Massively scalable object storage for unstructured data. AML service uses the general purpose v1 tier with LRS (locally-redundant storage). | [Block blob storage pricing](https://azure.microsoft.com/en-us/pricing/details/storage/blobs/)
Secrets management | [Azure Key Vault](https://azure.microsoft.com/en-us/services/key-vault/) | Safeguards secrets used by cloud apps and services. AML uses the Standard tier. | [Azure KeyVault pricing](https://azure.microsoft.com/en-us/pricing/details/key-vault/)
MLOps | [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) | Manages all aspects of your machine learning projects using advanced features like boards, pipelines, repos, test plans and artifacts. Combined with features from the Azure Machine Learning service, Azure DevOps provides the core backbone of end-to-end, comprehensive MLOps implementations. | [Azure DevOps pricing](https://azure.microsoft.com/en-us/pricing/details/devops/azure-devops-services/)
Tools | [Visual Studio Code](https://code.visualstudio.com/) |  Lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux. It comes with built-in support for JavaScript, TypeScript and Node.js and has a rich ecosystem of extensions for other languages (such as C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity). | Free
Tools | [Visual Studio](https://visualstudio.microsoft.com/) | Microsoft's core development environment that supports a wide range of workloads like web and cloud, Windows, mobile and gaming, Office and SharePoint, and Data Science and analytical applications. | [Visual Studio pricing](https://visualstudio.microsoft.com/vs/pricing/)

In addition to the compute resources mentioned above, the following might be used in a machine learning solution:
- [Data Science VMs](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/) - see [pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/windows/)
- [Data Lake Analytics](https://azure.microsoft.com/en-us/services/data-lake-analytics) compute resources - see [pricing](https://azure.microsoft.com/en-us/pricing/details/data-lake-analytics/)
- [HDInsight](https://azure.microsoft.com/en-us/services/hdinsight/) clusters - see [pricing](https://azure.microsoft.com/en-us/pricing/details/hdinsight/)


Other elements to be considered when estimating platforms, services, and tools costs are:
- [Azure support plans](https://azure.microsoft.com/en-us/support/plans/)
- [Azure reserved instances](https://azure.microsoft.com/en-us/pricing/reserved-vm-instances/) - make sure you understand the differences between ```Pay as you go``` vs. ```1 year reserved``` vs. ```3 years reserved```
- Cost variations depending on the type of Azure subscription used (Pay-as-you-go, CSP, EA etc...)