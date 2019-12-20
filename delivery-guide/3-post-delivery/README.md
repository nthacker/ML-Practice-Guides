# Monitoring model performance, handling model and data drift 

The following aspects should be considered when addressing the monitoring of models delivered during the project:

- Use a combination of Azure Machine Learning service and Azure DevOps features to [create end-to-end, transparent and manageable MLOps processes](https://docs.microsoft.com/en-us/azure/devops/pipelines/targets/azure-machine-learning)
- [Collec data for production models](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-access-data)
- [Monitoring and collect data for web service endpoints](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-enable-app-insights)
- Monitoring Azure Machine Learning service metrics with [Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-platform-metrics) - the metrics of interest are the ones from the ```Machine Learning Service``` Azure Monitor namespace
- Periodically inspecting the Azure Machine Learning service activity log

You should also be proactive when it comes to detecting model and data drift. The most common tasks you should perform are:
- Deploy tasks to monitor the performance of your models
- Define a baseline for each model's performance to detect model drifts early
- Deploy tasks to monitor your scoring data to detect drifts early
- Version and monitor your training data to detect drifts early


# Driving customer engagement post-delivery

- Ensure the customer starts to use the results of the project as early as possible in its business processes
- Engage with the customer in exploring business scenarios that are adjacent or derived from the ones addressed by the project
- Showcase project results to help your customer champions

# Identifying opportunities for new projects

On the path to successful delivery of the first project, you will probably have identified some additional opportunities to help the customer. As a part of wrapping of the delivery of the first phase, it's a good practice to capture these follow-on project opportunities so you can review with the customer in the context of a next steps discussion. This strategy is called "land and expand" as your initial project is how you "land" and the project opportunities represent ways to "expand" your engagement, such as:

- If the initial project was a PoC, a natural next project opportunity is the production solution (which might involve a pilot).
- If the initial project was a pilot, a natural next project could be to monitor the wider roll-out of the solution until it is fully in production.
- Improving the predictive performance of the delivered solution (remember, machine learning projects are highly iterative) by leveraging the learning acquired on the project about the domain, the algorithms explored or the data.
- Identifying and integrating new data sources that further enrich the capabilities of the delivered solution.
- Enhancing the robustness of the delivered solution. For example, you might augment the monitoring of the model in production to watch for more forms of performance degradation or for the impacts of data drift.
- Revisit the ideas collected during the envisioning session with the customer, and with a first understanding of the customer and the customer's data under you belt you will likely be able to provide better guidance on what is possible.
- Revisit any ideas put aside in a "parking lot" during discussions occurring at the architecture design session, that were not addressed by the first project.
