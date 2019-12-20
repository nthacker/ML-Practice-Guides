# Sizing and performance

## Sizing and performance in training

The following factors impact sizing and performance during the training stage:

- Available compute resources
- Data characteristics
- Algorithm and hyperparameter values combinations

### Sizing AML compute training clusters

AML compute training clusters are VM clusters managed by the Azure Machine Learning service. The most important parameters that control sizing are:

Name | Description
--- | ---
VM size | The size of the VM used as an individual cluster node (e.g. Standard_D2_v2).
Priority | The VMs used as node clusters can be either dedicated or low priority (case in which they are not guaranteed and jobs might be pre-empted).
Min/Max number of nodes | The sizing limits of the cluster. The cluster will always have the Min number of nodes and will never exceed the Max number of nodes.
Scale down idle seconds | Idle time to wait before scaling down the cluster to the minimum number of nodes.

Here are some best practices for sizing the compute resources:

- Use dynamic sizing (Min number of nodes < Max number of nodes) to optimize for both cost and performance
- When acceptable, use Min number of nodes = 0 to make sure the compute cluster is completely decommissioned when not needed. Keep in mind though that there will be a startup penalty each time a job is submitted and the cluster has zero running nodes.
- Chose the VM edition of the cluster node based on the complexity and resources requirements of your individual runs. You should also factor in the data your runs have to deal with (in terms of size and complexity of transformations).
- When using automated ML, size your cluster based on the maximum number of scenarios (algorithms and hyperparamters combinations) to be considered.
- When using machine learning libraries that use GPU resources (e.g. TensorFlow, Keras, PyTorch, and deep learning in general) use appropriate VM editions to make sure GPU acceleration is available to them.

Remember that you will always need to make a tradeoff between cost and speed. Scaling your compute clusters will generally yield improved training performance provided that your workloads spawn a high enough number of runs and child runs to take proper advantage of the increased compute resources.

### Sizing attached compute for training

In addition to AML compute resources, the following compute resources can be used:
- [Data Science VMs](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/)
- [Azure Databricks](https://azure.microsoft.com/en-us/services/databricks/) clusters
- [Data Lake Analytics](https://azure.microsoft.com/en-us/services/data-lake-analytics) compute resources
- [HDInsight](https://azure.microsoft.com/en-us/services/hdinsight/) clusters

In the case of PoC/Pilot projects, you will use these compute resources mostly in cases where the customer already has an investment in such environments. The same general principles apply as in the case of AML compute resources (combined with specific aspects for each environment). A discussion on the specifics of sizing for these resources is outside the scope of this guide.

### Assessing the impact of data

Besides the complexity of the machine learning algorithms involved in your workloads, data plays an important role in sizing requirements and performance. You will need to factor in the various stages of data processing as follows:

- Raw data - determine the size of raw data (data loaded into the machine learning pipeline)
- Cleansed data - determine the size of the cleansed data (in case your machine learning pipeline performs cleansing tasks in addition to the ones involved in the initial data preparation process)
- Enriched data - determine the size of the enriched data (in case your machine learning pipeline performs feature engineering tasks in addition to the ones involved in the initial data preparation process)

Remember that some of the workloads (like automated ML, for example) perform additional internal  data intensive processing that need to be factored in when evaluating compute resource sizing and performance. 

### Number of trained machine learning models

The resulting number of trained machine learning models has a direct dependency on the number of algorithms taken into consideration and the combinations of hyperparameter values. These algorithm + hyperparameter values combinations can be either implemented manually in your workloads or generated via automated ML. In the first case, you have direct access to all the information needed to evaluate the complexity of your training workloads. In the second case, you have to make sure you properly understand the implications of the various automated ML parameters that govern the generation of such combinations.


## Sizing and performance in scoring

The following factors impact sizing and performance during the scoring stage:

- Available compute resources
- The type of scoring - real-time or batch
- The type of environment - dev/test or production
- Data characteristics

### Sizing scoring clusters

There are [multiple choices](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-deploy-and-where) for compute targets used in scoring tasks. For PoC/Pilot projects, most of the time you will have to decide between the following options:

Name | Recommended in
--- | ---
[Azure Container Instances](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-deploy-and-where#aci) | Real-time scoring, dev/test scenarios, no GPU requirements.
[Azure Kubernetes Service](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-deploy-and-where#aks) | Real-time scoring, production scenarios, CPU or GPU requirements.
[Azure Machine Learning Compute](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-run-batch-predictions) | Batch scoring, production, CPU or GPU requirements.

Here are some best practices for sizing the compute resources:

- Use dynamically sized clusters (AKS or AML compute) to provide elasticity, especially in the case of non-linear scoring workloads.
- Chose the VM edition of the cluster node based on the complexity and resources requirements of the scoring process. You should also factor in the data your scoring processes have to deal with (in terms of size and complexity of transformations).
- When using machine learning libraries that use GPU resources (e.g. TensorFlow, Keras, PyTorch, and deep learning in general) use appropriate VM editions to make sure GPU acceleration is available to them.

Remember that you will always need to make a tradeoff between cost and speed. Scaling your compute clusters will generally yield improved scoring performance provided that your workloads spawn a high enough number of scoring jobs to take proper advantage of the increased compute resources.

The table presented above can be viewed also as a simple decision matrix for deciding on the type of scoring compute to use. When batch scoring is implied, AML compute is the first choice for both PoC and Pilot type projects. When real-time scoring is implied, ACI is the choice to demonstrate the shape of the outcome (scoring REST service endpoints) for both PoC and Pilot projects. Since Pilot projects imply production environments as well, the final result should be deployed in most of these cases to an AKS cluster.

Estimate real-time scoring performance

The most common metric used to measure real-time scoring performance is the number or requests/unit of time (e.g. requests per second) that can be handled by the web service endpoint. The factors that influence the final value of the metric are:

- The amount of data payload per scoring call
- The complexity of the scoring process (e.g. requiring additional data transformation before calling the trained model)
- The scalability properties of the compute resources allocated (including VM sizes, number of cluster nodes)

Estimate batch scoring performance

The most common metric used to measure batch scoring performance is the number of cases/unit of time (e.g. cases scored per second) that can be handled by the scoring backend. The factors that influence the final value of the metric are:

- The average size of the scoring batch (be aware the actual sizes might vary quite a lot, depending on the specific problem you are addressing)
- The complexity of the scoring process (e.g. needing to load data from different systems and requiring additional data transformation before calling the trained model)
- The complexity of the output (e.g. needing to save the results of the scoring to different systems)
- The volume of compute resources allocated


