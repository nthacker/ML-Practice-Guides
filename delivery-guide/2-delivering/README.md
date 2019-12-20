# Starting with a PoC or a Pilot

When embarking on a machine learning project, it is often useful to start by delivering a Proof of Concept (PoC) or a Pilot. In this context, it is important to keep the distinction between PoC and Pilot clear – a PoC should never be considered for direct deployment into production, whereas a pilot should be constructed with a production release in mind.

For example, in a machine learning PoC you may not even touch the customers actual data set and instead use similar data from open data sets to show what the value of the predictive capabilities and to tangibly illustrate how they would be applied in the context of a running solution. In a pilot, however, you would want to start with the customer’s actual datasets because the goal is to end up with a model, that if successful, would flow into the production solution.

A pilot solution is a production-ready product whose influence is limited in scope (e.g, a targeted rollout), customer base, or capacity. A well-executed pilot will give the customer a better understanding of how the project goals will be successful, while providing them with a production-grade starting point. Since a successful pilot will be scaled up to the final production solution, it is important to create the pilot following best practices.

For details on how to plan and execute a PoC or a Pilot, see the [AML PoC and Pilot Process Guide](../../poc-and-pilot-guide/README.md).

# MLOps mindset for delivery

When starting a machine learning project there is a lot of temptation (especially from data scientists) to jump right into the core of the problem and start developing and testing models. While this is certainly important (even critical) for the success of the project, it is equally important to enforce project discipline right from the beginning by employing classical DevOps procedures (referred as MLOps when applied to machine learning projects).

Approaching the entire project this way, right from the beginning, is what we mean by having an MLOps mindset for delivery. At a minimum, the following principles should be enforced:

- All source code is handled by version control, including the code to train, evaluate, and score machine learning models
- All machine learning related artifacts are properly managed and versioned. The list includes:
  - Training and testing data sets
  - Trained machine learning models
  - Deployment images and actual deployments
- All processes are handled by DevOps pipelines. The list includes:
  - Data preparation
  - Model training
  - Model evaluation
  - Model deployment

The typical combination for materializing an MLOps mindset for delivery is Azure Machine Learning service and Azure DevOps. The two services complement each other and combining them enables you to drive a process that minimizes the risk of failure and non-delivery. 

You should define the coordinates of your MLOps approach at the very beginning of the project and implement all necessary elements as early as possible. You should also enforce project discipline and make sure everybody, including the most creative members of the team, adhere to the core rules of source control, work items management, pipeline-based model training and deployment, and full traceability of the entire delivery process.

An end-to-end example of a solution built with an MLOps mindset can be followed in the [MLOps Microsoft Cloud Workshop](https://github.com/microsoft/mcw-ml-ops).

# Delivering the project

> **Note**: This section provides detailed technical guidance. If you are only interested in the high level approach for delivering a machine learning project, you can skip the sections pointed by the links.

The actual technical delivery of the project involves multiple processes, depending on the specific requirements of the customer. Some of the most widely encountered ones are:

- [Data acquisition and understanding](processes/data-acquisition-understanding.md)
- [Feature engineering](processes/feature-engineering.md)
- [Model training and evaluation](processes/model-training-evaluation.md)
- Training and evaluation using the Azure Machine Learning studio visual interface - use the **Designer** section of the new [Azure Machine Learning studio](https://ml.azure.com)
- [Automating training and evaluation with Automated ML](processes/automl.md)
- [Modularizing solutions with pipelines](processes/modularization-pipelines.md)

# Operationalizing the results

How you operationalize the results depends on the type of project you have undertaken.

If your project was a PoC, operationalizing the results actually means capturing the learnings from the PoC implementation, specifically it is documenting how the PoC:

- addresses identified risks
- proves out the capability of untested algorithms, data or approaches
- learnings should inform a production implementation effort

Remember, it is never a good practice to take the artifacts created for a PoC and directly use them in the production. It is the learnings acquired during the PoC that you want to take away. 

For a PoC or pilot, how you operationalize the machine learning project centers around your handling of the model:
- If the model will be integrated into other application components for validation during the PoC, then a deploying your model as an HTTP web service is good choice. For a PoC that whose scope is not addressing scalability, you can use  Azure Machine Learning to containerize and deploy your model to an Azure Container Instance. If your PoC scope includes scalability validation or you are performing a pilot, then you should use Azure Machine Learning to deploy the model to Azure Kubernetes Service, which will provide your web service scale-out capabilities. 
- If the model will be used for batch scoring in a back-end process, then you should ensure that the model used for the PoC or pilot is available within the Azure Machine Learning model registry. The application that uses the model for batch scoring (e.g., a scheduled Azure Databricks Notebook) can then retrieve the latest model from the registry and apply it for scoring.

> **Note**: The reminder of this section provides detailed technical guidance. If you are only interested in the high level approach for delivering a machine learning project, you can skip the sections pointed by the links.

Operationalization typically involves processes like:

- [Deploying trained models to various targets](processes/deployment-targets.md)
- [Standardizing deployed models with ONNX](processes/standardization-onnx.md)
- [Managing model versions](processes/model-version-management.md)
- [Monitoring deployed models with data collection and telemetry](processes/monitoring.md)

# Security, trust and responsible AI 

Security is one of the most important aspects of machine learning projects. Due to the complexity of such projects, the potential attach surface is significant. See the [security checklist](./../4-templates-and-checklists/README.md) for a detailed list of security areas you have to address when delivering a project.

In many projects, the ability to easily explain the end-to-end process is one of the key requirements. This addresses one of the top customer concerns - the fear to fail in understanding the inner workings of the solution at various levels of detail. While being a challenge, it is in the same time a big opportunity to earn the trust of your customers.

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


# Driving customer engagement during delivery

The following aspects are relevant to driving customer engagement in general:

- Ensure the project refers to aspects of a real business pain, that has been validated and confirmed with the proper decision making level in the customer organization
- Identify at least one business stakeholder in the customer organization
- Identify early in the project real and confirmed/validated customer concerns related to sizing, performance, availability, scalability, security, explainability, maintainability, extensiblity, and cost estimation - these are critical issues to address 

## Driving engagement during the delivery of the project

- Explain every stage of the project and make sure every milestone is and continues to be aligned with business pain points
- Help the customer understand how the business pain points are solved and how can this be measured/proven
- Ensure the customer starts to use the results of the project in its business processes as early as possible 
- Help the customer identify effective ways to validate the results of the project


# Handling change management during delivery
Machine learning projects, like more traditional software projects, will evolve during the course of the delivery as the act of delivering the solution improves the overall understanding of the problem domain and this leads to potential changes that need to happen during the course of the project. 

Change management in machine learning projects can be potentially more complex than in traditional projects. This is primarily due to the fact that machine learning projects require iteration and flexibility. There are often many unknowns at the project start, that despite your best efforts will have to be addressed in the course of the project with proper change management. Some examples of these challenges to watch out for include:

- Data-related change requests: the data the client thought they had during design, needs significantly more preparation work, needs to be integrated in unexpected ways, does not exist or does not have the insights needed to make the desired predictions. 
- Fuzzy change requests: in learning more about the problem being solved by the project, the customer may realize they did not correctly understand the original problem, the domain, or the intended goal. For example, at the outset the customer might be adamant that they want a binary, true/false or yes/no outcome from the machine learning model. But over the course of the project, it becomes clear that having the percentage confidence in yes versus no is actually what the solution needs.   

How you handle change during a project is largely related to what flexibility you have built-in to your agreement with the customer. You can think of all software projects as managed by three levers, consisting of:

- Scope (Features)
- Budget
- Timeline

Each lever is one you can, and mostly likely will, adjust on the way to successful project delivery. For example, after understanding their own data better the client might ask for additional data preparation or new model capabilities which increase the scope of the project. You need to decide if this additional scope can be addressed by taking an equivalent feature or set of features out of scope, or if they will agree to an increase in budget, or if the budget allows if the increase in scope can still be accomplished within the desired timeline. In the most extreme cases, adding the new scope will require augmenting scope, budget and timeline. This can pose a risk to project completion, especially if the client is always allowed to add such scope, the project just keeps getting extended and completion gets further out of reach. It almost goes without saying that for any change the options available to both your and your client are to: 

- Decide not to implement the requested change.
- Capture the change request, but put it aside for a future project.
- Smoothly steer the project over time so it becomes in alignment with the desired change.
- Disrupt the project to incorporate the critical change.


# CE (Continuous Explanation) mindset- how to make sure the business understands what’s being delivered

One of the significant risks of any machine learning project is the lack of understanding by the business stakeholders and users of the results being produced. This can occur at any point in time during and after delivery and can happen even if up to some point the outcomes of the project were properly understood.

You should keep in the back of your mind the following goals:
- Communicate regularly with business stakeholders and users about the results being produced during delivery - explain every output, every correlation, every risk or uncertainty associated with them.
- Evaluate the customer's level of understanding resulting from the above mentioned communication.
- Never assume implicitly a person understands what you are presenting as results of the project (or a stage of the project). Having a clear and complete understanding is only one of a very long list of reasons they might not challenge you in this respect.
- Make sure the scope of the project and the estimation of effort include a proper amount of resources dedicated to present the results of the machine learning models in an understandable, actionable, and measurable way (e.g. with detailed dashboards, charts, and other graphical representations).
- Make sure it's clear for everybody how results can and should be measured and which are the commonly agreed quality metrics used to decide the level of success for the project.