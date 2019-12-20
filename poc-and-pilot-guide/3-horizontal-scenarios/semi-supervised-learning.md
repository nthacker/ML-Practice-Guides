# Semi-supervised learning

The semi-supervised learning approach combines both the supervised and the unsupervised approaches. It uses a small amount of labeled data and a (much) larger amount of unlabeled data.

The practical case for semi-supervised learning is based on the difficulty to acquire labeled data. This usually requires either human intervention (performed by individuals with appropriate skills levels) or execution of physical actions (e.g. experiments in chemistry and/or physics). Both types of tasks incur significant costs as opposed to acquiring unlabeled data which is usually inexpensive. Hence, the value of semi-supervised learning.

Examples of semi-supervised learning algorithms include:
- Self-training - uses the model's predictions on unlabeled data to derive information that can be used during training
- Multi-view training - based on training multiple models that have different views on data (e.g. features used, models architecture, or training data)
- Self-ensembling - similar approach as in multi-view training except it uses a single model with different hyperparameter values instead of multiple different ones