# Project plan template

Machine learning projects can be executed using one of many lifecycles like the Cross Industry Standard Process for Data Mining ([CRISP-DM](https://wikipedia.org/wiki/Cross_Industry_Standard_Process_for_Data_Mining)) or Knowledge Discovery in Databases ([KDD](https://wikipedia.org/wiki/Data_mining#Process)) which fundamentally address the reality that machine learning projects are highly iterative approaches moving between the conceptual stages of requirements gathering, data collection, data preparation, modeling, model deployment and model maintenance, often exhibiting cycles that loop back to a previous stage as details are refined.

In this guide, we recommend the use of the [Microsoft Team Data Science Process](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/agile-development) (TDSP) with an agile approach. 

The five major stages of TDSP are as follows and are illustrated in the subsequent diagram:
- [Business understanding](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/lifecycle-business-understanding): Specify the key variables that are to serve as the model targets and whose related metrics are used determine the success of the project; Identify the relevant data sources that the business has access to or needs to obtain.
- [Data acquisition and understanding](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/lifecycle-data): Produce a clean, high-quality data set whose relationship to the target variables is understood. Locate the data set in the appropriate analytics environment so you are ready to model; Develop a solution architecture of the data pipeline that refreshes and scores the data regularly.
- [Modeling](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/lifecycle-modeling): Determine the optimal data features for the machine-learning model; Create an informative machine-learning model that predicts the target most accurately; If delivering a pilot, create a machine-learning model that's suitable for production.  If delivering a PoC, create a machine-learning model that addresses that proves out the feasibility and addresses identified risks.
- [Deployment](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/lifecycle-deployment): Deploy models with a data pipeline to a production or production-like environment for final user acceptance. 
- [Customer acceptance](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/lifecycle-acceptance): Finalize the project deliverables: Confirm that the pipeline, the model, and their deployment in a production environment satisfy the customer's objectives for the pilot or PoC.

![The TDSP lifecycle](media/tdsp-lifecycle2.png)

A machine learning project executes the major stages of TDSP using an agile methodology and as such can leverage project management tools designed for agile delivery. 

## Using the Azure DevOps Project Template

In this guide, we recommend the use of Azure DevOps and a work item process template derived from the Agile work item process that is included with Azure DevOps. This approach provides support for the concepts of Features, User Stories, Tasks and Bugs of the traditional agile process, but modified to use the terminology of TDSP.

A typical starter project using this TDSP process template in Azure DevOps has the follow structure of work items.

![TDSP work items in Azure DevOps](media/azure-devops-project-items.png)

To accomplish this structure, the setup process of your Azure DevOps environment involves the following two steps:

1. Configure your Azure DevOps environment with a TDSP agile process template. This typically only needs to be done once. If you work within multiple Azure DevOps organizations, you will need to do this once per organization.

2. Create a new Azure DevOps project and populate the TDSP work items. This needs to be done for each new project. As a bare minimum we recommend starting any new project with the following work items:

    | Work Item Type	| Title	|
    | --- | --- |
    |TDSP Project	| Machine Learning Project|
    | Business Understanding | Collect requirements and opportunities | 
    | TDSP Substage  |Perform envisioning session	|
    | TDSP Substage  |Perform architecture design session (ADS)	|
    | TDSP Substage  |Identify candidate PoC's or pilot	|
    | TDSP Substage  |Select PoC or Pilot	|
    | TDSP Substage  |Gather detailed requirements	|
    | TDSP Substage  |Collect inventory of data assets	|
    | Data Acquisition	| Acquire data	|
    | TDSP Substage  |Load data to Azure Storage	|
    | TDSP Substage  |Clean and prepare data for modeling	|
    | TDSP Substage  |Implement data preparation pipeline	|
    | Modeling	| Create models	|
    | TDSP Substage  |Create model in Jupyter notebook	|
    | TDSP Substage  |Evaluate and document model performance	|
    | Deployment	| Operationalize models	|
    | TDSP Substage  |Operationalize data pipeline	|
    | TDSP Substage  |Deploy model web services	|
    | TDSP Substage  |Collect & monitor model performance	|
    | TDSP Substage  |Monitor data drift	|
    | Customer Acceptance	|Finalize the project deliverables	|
    | TDSP Substage  |Confirm customer requirements satisfied	|
    | TDSP Substage  |Complete hand-off to customer	|

For step-by-step instructions on how to create the agile-derived TSDP process template and then how to create a new Azure DevOps project that uses this template (as illustrated above), see [Using an agile TDSP template](https://docs.microsoft.com/en-us/azure/machine-learning/team-data-science-process/agile-development#use-an-agile-tdsp-work-template)
