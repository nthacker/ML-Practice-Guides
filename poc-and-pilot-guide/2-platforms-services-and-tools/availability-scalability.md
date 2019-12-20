# Availability and scalability

Trained machine learning models can be used in one of the following basic patterns:

- [Real-time scoring](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-consume-web-service) - each case (or set of cases) are scored in real-time by calling a web service endpoint.
- [Batch scoring](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-run-batch-predictions) - large sets of cases are scored in the background by running batches.

Before getting into the details of availability and scalability of each pattern, you should become familiar with the [standard Azure Machine Learning resource quotas](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-manage-quotas). This will help you better understand which are the limits of availability/scalability in Azure Machine Learning service.

Availability and scalability will depend on:

- The sizes of VMs used in your scoring environments
- The type of environment providing the compute resources (ACI, AKS, AML compute)
- Various service limits that refer to these compute resources

**Note**

In addition to ACI, AKS, and AML compute resources, other types of compute resources can be used as well in your PoC/Pilot projects. A discussion on the specifics of availability and scalability of these additional resources is outside the scope of this guide.

## Availability in real-time scoring

In this case, availability refers to the availability of the scoring web service endpoint to service scoring calls. The following aspects influence the availability of your scoring service:
- [ACI quotas and limits](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-quotas)
- [ACI region availablity](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-region-availability)
- [AKS quotas, limits, and region availablity](https://docs.microsoft.com/bs-cyrl-ba/azure/aks/quotas-skus-regions)

## Availability in batch scoring

In this case, availability refers to the availability of the compute resources used by the backend batch scoring processes. In the case of AML compute, the [standard Azure Machine Learning resource quotas](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-manage-quotas) rules apply.

## Scalability in real-time scoring

In this case, scalability refers to the capacity of adding new compute resource units to increase the number of real-time scoring requests serviced in any given unit of time. The following aspects influence the scalability of your scoring service:

- [AKS scalability](https://docs.microsoft.com/bs-cyrl-ba/azure/aks/concepts-scale)
- ACI scalability - ACI does not have any built-in support for scalability. You can [use an AKS virtual node to provision pods inside ACI](https://azure.microsoft.com/en-us/solutions/architecture/scale-using-aks-with-aci/).

## Scalability in batch scoring

In this case, scalability refers to the capacity of extending the amount of compute resources used by the backend batch scoring process. In the case of AML compute, the [standard Azure Machine Learning resource quotas](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-manage-quotas) rules apply.