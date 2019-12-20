# Data acquistion and understanding

*Big Data* has become part of the lexicon of organizations worldwide, as more and more organizations look to leverage data to drive more informed business decisions. With this evolution in business decision-making, the amount of raw data collected, along with the number and diversity of data sources, is growing at an astounding rate. Raw data, however, is often noisy and unreliable and may contain missing values and outliers. Using such data for modeling can produce misleading results. For the data scientist, the ability to combine these large, disparate data sets into a format more appropriate for conducting advanced analytics is an increasingly crucial skill. In the field of data science, this skill is commonly known as **data wrangling**.

## What is data wrangling?

Data wrangling, also referred to as data munging or data transformation, is the process of cleaning, restructuring and enriching raw data to transform it into a format more suitable for use in common data science tasks, such as advanced data analytics and machine learning.

Real-world data is frequently gathered from multiple sources using varying processes, and collected in several different formats and data stores. This data may contain irregularities or corrupt data which can compromise the quality of the dataset, including:

- Incomplete data lacking attributes or containing missing values
- Noisy data with erroneous records or outliers
- Inconsistent data containing conflicting records or discrepancies

To build quality predictive models, data scientists must have quality data. This is where data wrangling comes into play. The process allows for the identification of data quality issues and decisions about the appropriate data processing and cleaning steps necessary to improve data quality, before using it for modeling. Data scientists adept at this process of organizing and structuring data prior to performing more in-depth analysis can help drive better insights from larger amounts of data, and typically do it in less time.

> The [Azure Machine Learning Data Prep SDK for Python](https://docs.microsoft.com/python/api/overview/azure/dataprep/intro?view=azure-dataprep-py) was designed to help you explore, cleanse, and transform data from machine learning workflows.

Similar to many other data analytics processes, data wrangling is iterative. The process typically follows a set of generalized steps, beginning with data discovery and exploration, followed by data transformation tasks, such as restructuring, cleansing, and augmenting, and ending with validating and publishing to a resultant dataset for future use. 

## Discover and explore

Before using data for building models and performing deeper analysis, it is necessary to understand the dataset, what it contains, how it is structured, and what issues may exist within it. The discovery and exploration step uses data summarization and visualization techniques to audit the dataset, to gain a better understanding of data quality and structure and highlight important and interesting aspects of the dataset. The information derived from this step informs how you go about transforming data by providing the details required to process data before it is ready for modeling.

This step begins with extracting the data in its raw form from the data source and using various techniques, such as data visualizations, data aggregation, and sorting, to describe and explore the data and uncover issues. The general quality of a dataset can be checked by:

- Examining the number of records
- Inspecting the number of attributes (or features as they are more commonly known in data science terms)
- Reviewing the feature data types (nominal, ordinal, or continuous)
- Checking features for and counting the number of missing values
- Looking at how well-formed the data is (e.g., checking that column and line separators always correctly separate columns and lines in TSV or CSV files)
- Checking for inconsistent data records, such as checking the range of allowable values for a feature (e.g., If the data contains student GPAs, check if the GPA is in the designated range, say 0.0 to 4.0)

An excellent place to start is to inspect the data visually. In the Python code below, sample crime data is read into an [Azure ML DataPrep Dataflow class](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep.dataflow?view=azure-ml-py), and then the first 5 records are displayed using the `head()` function on the Dataflow.

```python
import pandas as pd
import azureml.dataprep as dprep

# Path for dataset
file_crime_dirty  = './data/crime-dirty.csv'

# Read the crime data into a Dataflow
crime_dirty = dprep.auto_read_file(path=file_crime_dirty)

# Display the first 5 records
crime_dirty.head(5)
```

![The first 5 records of the crime_dirty DataFrame are displayed.](media/crime-dirty-head-5.png "Crime data")

Inspecting the data contained within the dataset allows you to observe the types of data and some potential issues. For example, notice in the third record above, the `X Coordinate` field contains `NaN`, meaning the record contains a missing value.

To help you quickly perform many of the essential quality checks and gain a better understanding of the properties of your dataset, the [Azure ML Data Prep SDK](https://docs.microsoft.com/python/api/overview/azure/ml/intro) offers **data profiles**. Data profiles help you glimpse into the column types and summary statistics of a dataset. They can be accessed by using the `get_profile()` method on a Dataflow. In the example below, we profile the data within the sample crime dataset.

```python
# Profile the data
crime_dirty.get_profile()
```

![Output of the get_profile() method.](media/data-profiles-output.png "Data profiles")

## Transform

Using data discovery and exploration, you gain a better understanding of your data. The transformation step of the data wrangling process allows you to address the issues found during the discovery step. The data processing and preparation that occurs during this step involves data restructuring, normalization and cleansing, and augmentation. Transformation is about reshaping raw data into a form that can be more quickly and accurately analyzed.

### Restructure

The restructuring step is about organizing and integrating data collected from various sources. The purpose of this step is to make raw data derived from disparate sources and formats more consistent and accurate. Information revealed during the discovery and exploration step is used to restructure data in a way that allows combination, computation, and analysis to be conducted more easily. Rows may be appended, and columns and rows may be split or combined.

### Cleanse

In the previous steps, you identified data quality issues, such as null or missing values, out of range values, and inconsistent data formatting. During the data cleansing step, you address these issues, performing tasks such as standardizing and normalizing values, correcting or removing corrupt or inaccurate records from the dataset, fixing typographical errors and handling null values. The goal of this step is to increase the overall quality of the data.

### Augment

Augmenting is where you look at how additional data could be used to enrich your dataset. At this step, you evaluate how you can leverage data you already have to make the dataset better and consider what other information could better inform your decision-making process.

## Validate

The validation step of the data wrangling process is about verifying the consistency and quality of data. Checks during this step can be strict or fuzzy and might include checking for uniform distribution of features that should be normally distributed and cross comparing data against validated datasets (e.g., ensuring state abbreviations or postal codes are valid)

## Publish

The ultimate goal of data wrangling is to create a dataset that can be easily consumed by downstream processes and users. The wrangled data is published to a shared data store, such as Azure Data Lake Storage v2, where users and software can consume it for advanced analytics and machine learning.

# Accessing data from various Azure services and working with AML datastores

Azure Machine Learning (AML) service uses **[datastores](https://docs.microsoft.com/azure/machine-learning/service/how-to-access-data)** to read and write data to and from various Azure storage services. Datastores are references that point to Azure storage services, such as a blob container. Essentially, a datastore is an abstraction over an Azure storage service that stores the information required to connect to it. This abstraction simplifies the process of accessing data stored within the storage service. Using datastores, you to connect to the underlying storage service by name, and do not need to remember connection information and secrets used to connect to data sources.

Also, datastores provide a storage service access mechanism that is independent of your [compute](https://docs.microsoft.com/azure/machine-learning/service/concept-compute-target) location. In Azure Machine Learning, the term **compute** (or **compute target**) refers to the machines or clusters that perform the computational steps in your machine learning pipeline. Compute location-independence means you can easily change your compute environment without changing your source code. Azure Machine Learning workflows ensure your datastore locations are accessible and made available to your compute context.

Throughout this article, we examine how datastores allow data access from the supported Azure storage services. We also review the management of datastores within your AML workspace using the Azure Machine Learning SDK for Python.

## Supported Azure storage services

Data is frequently stored in various formats and can be structured, semi-structured, or unstructured. AML service provides the flexibility to access multiple existing data sources by supporting the registration of the following Azure storage services as datastores:

- [Azure Blob Container](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview)
- [Azure File Share](https://docs.microsoft.com/azure/storage/files/storage-files-introduction)
- [Azure Data Lake](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-overview)
- [Azure Data Lake Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)
- [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Azure PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview)
- [Databricks File System](https://docs.azuredatabricks.net/user-guide/dbfs-databricks-file-system.html)

> **Note**: Use of blob storage and blob datastores is the recommended approach, at this time. You can use either standard and premium storage, depending on your needs. Although more expensive, premium storage provides faster throughput speeds, which may help to improve performance during training runs, specifically if you are training against large data sets.

The remaining sections of this article provide specific details about how to register and access data within each of the supported Azure storage services.

## Working with datastores

To work with datastores in an AML workspace, you use the `Workspace` and `Datastore` classes in the [Azure Machine Learning SDK for Python](https://docs.microsoft.com/python/api/azureml-core/azureml.core.datastore(class)?view=azure-ml-py).

To provide a clean environment for the examples that follow, we are using a new AML workspace. The new workspace is created using the [Azure Machine Learning SDK for Python](https://docs.microsoft.com/python/api/overview/azure/ml/intro?view=azure-ml-py), following the instructions provided in the [Environment Setup article](../intro/environment-setup.md#Option-3-Python-SDK) of this guide.

> **Note**: You can also use an existing workspace by replacing `Workspace.create()` in the command below with `Workspace.from_config()` in a notebook within your existing workspace.

Use the following command to create the new workspace from a Jupyter notebook, adding in your subscription ID:

```python
import azureml.core
from azureml.core import Workspace

ws = Workspace.create(name='aml-workspace',
                      subscription_id='<azure-subscription-id>',
                      resource_group='aml-rg',
                      create_resource_group=True,
                      location='eastus2'
                     )
```

![Output of the SDK Workspace.create() command above.](media/create-workspace-sdk.png "Create workspace")

The workspace deployment process includes the creation of a new storage account, as you can see within the output from the command above. Within that storage account, both a blob container and file store are created and automatically registered as datastores in the workspace.

The SDK supports the following categories of datastore operations:
- List datastores
- Get an individual datastore
- Get or set the default datastore
- Register a new datastore
- Unregister a datastore
- Upload and download data

# Load, transform, and write data with Azure Machine Learning and the AML Data Prep SDK

The [Azure Machine Learning (AML) Data Prep SDK](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py) provides the core framework for loading, exploring, analyzing, and preparing data in Azure Machine Learning. Using the Data Prep SDK, you can read data from files and other data sources, apply transformations to those data, and write files to supported locations.

In this article, we review the various Data Prep SDK methods for reading and writing data to and from multiple file types and data sources. Methods for performing common data transformations and manipulations are also covered.

## Supported data sources

The Data Prep SDK supports data ingestion from multiple types of input data, including various file types and SQL data sources.

The table below lists the supported file types, and the functions used to read them. The function names link to the relevant Data Prep SDK documentation for each method.

| File type | Function | Description |
| --------- | -------- | ----------- |
| Auto-detect | [auto_read_file()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py&viewFallbackFrom=azure-dataprep-py#auto-read-file-path--filepath--include-path--bool---false-----azureml-dataprep-api-dataflow-dataflow) | Analyzes the file(s) at the specified path and returns a new Dataflow containing the operations required to read and parse them. |
| CSV | [read_csv()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-csv-path--filepath--separator--str--------header--azureml-dataprep-api-dataflow-promoteheadersmode----promoteheadersmode-constantgrouped--3---encoding--azureml-dataprep-api-engineapi-typedefinitions-fileencoding----fileencoding-utf8--0---quoting--bool---false--inference-arguments--azureml-dataprep-api-builders-inferencearguments---none--skip-rows--int---0--skip-mode--azureml-dataprep-api-dataflow-skipmode----skipmode-none--0---comment--str---none--include-path--bool---false--archive-options--azureml-dataprep-api--archiveoption-archiveoptions---none--infer-column-types--bool---false--verify-exists--bool---true-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read and parse CSV and other delimited text files (TSV, custom delimiters like semicolon, colon, etc.). |
| Excel | [read_excel()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep#read-excel-path--filepath--sheet-name--str---none--use-column-headers--bool---false--inference-arguments--azureml-dataprep-api-builders-inferencearguments---none--skip-rows--int---0--include-path--bool---false--infer-column-types--bool---false--verify-exists--bool---true-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read Excel files. |
| Fixed-width | [read_fwf()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep#read-fwf-path--filepath--offsets--typing-list-int---header--azureml-dataprep-api-dataflow-promoteheadersmode----promoteheadersmode-constantgrouped--3---encoding--azureml-dataprep-api-engineapi-typedefinitions-fileencoding----fileencoding-utf8--0---inference-arguments--azureml-dataprep-api-builders-inferencearguments---none--skip-rows--int---0--skip-mode--azureml-dataprep-api-dataflow-skipmode----skipmode-none--0---include-path--bool---false--infer-column-types--bool---false--verify-exists--bool---true-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read and parse fixed-width data. |
| JSON | [read_json()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-dataprep-py#read-json-path--filepath--encoding--azureml-dataprep-api-engineapi-typedefinitions-fileencoding----fileencoding-utf8--0---flatten-nested-arrays--bool---false--include-path--bool---false-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read JSON files. |
| Parquet | [read_parquet_file()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-parquet-file-path--filepath--include-path--bool---false--verify-exists--bool---true-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read Parquet files. |
| Text | [read_lines()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep#read-lines-path--filepath--header--azureml-dataprep-api-dataflow-promoteheadersmode----promoteheadersmode-none--0---encoding--azureml-dataprep-api-engineapi-typedefinitions-fileencoding----fileencoding-utf8--0---skip-rows--int---0--skip-mode--azureml-dataprep-api-dataflow-skipmode----skipmode-none--0---comment--str---none--include-path--bool---false--verify-exists--bool---true-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read text files and split them into lines. |
| Compressed CSV | [read_csv()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-csv-path--filepath--separator--str--------header--azureml-dataprep-api-dataflow-promoteheadersmode----promoteheadersmode-constantgrouped--3---encoding--azureml-dataprep-api-engineapi-typedefinitions-fileencoding----fileencoding-utf8--0---quoting--bool---false--inference-arguments--azureml-dataprep-api-builders-inferencearguments---none--skip-rows--int---0--skip-mode--azureml-dataprep-api-dataflow-skipmode----skipmode-none--0---comment--str---none--include-path--bool---false--archive-options--azureml-dataprep-api--archiveoption-archiveoptions---none--infer-column-types--bool---false--verify-exists--bool---true-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to extract, read and parse CSV and other delimited text files from a ZIP archive. |

The Data Prep SDK also supports the following non-file data sources:

| Data Source | Function | Description |
| ----------- | -------- | ----------- |
| Pandas DataFrame | [read_pandas_dataframe()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-pandas-dataframe) | Creates a new Dataflow based on the contents of a given pandas DataFrame. |
| Parquet Dataset | [read_parquet_dataset()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-parquet-dataset-path--filepath--include-path--bool---false-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow with the operations required to read Parquet Datasets. |
| PostgreSQL | [read_postgresql()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-postgresql-data-source--databasesource--query--str-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow that can read data from a PostgreSQL database by executing the query specified. |
| SQL | [read_sql()](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep?view=azure-ml-py#read-sql-data-source--databasesource--query--str-----azureml-dataprep-api-dataflow-dataflow) | Creates a new Dataflow that can read data from a Microsoft SQL or Azure SQL database by executing the query specified. |

## The Dataflow class

An important concept to understand as you begin working with data using the AML Data Prep SDK is the abstraction provided by the [Dataflow class](https://docs.microsoft.com/python/api/azureml-dataprep/azureml.dataprep.dataflow?view=azure-ml-py). Similar to a resilient distributed dataset (RDD) in Spark, a `Dataflow` represents an optimized execution plan for a series of lazily-loaded, immutable operations on the underlying data. "Lazily-loaded" means that data is not read from the source until specific action methods are called, such as `head()`, `to_pandas_dataframe()`, `get_profile()` or the write methods. This approach allows AML to optimize data retrieval based on the transformation operations or steps added to the `Dataflow`. Calling an action method on the Dataflow results in the execution of all defined operations. The resultant dataset is a [Pandas DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html).

## Load data

To load data with the Data Prep SDK, use the `read_*` methods listed above. Each of these methods returns a `Dataflow` object that initially contains the steps required to read and parse data from the target data source. As you apply transformations to the data retrieved from a data source, steps are added to the `Dataflow`. When an action method, such as `write_to_csv()` is finally called, the Data Prep SDK determines the most efficient way to execute all of the steps on the `Dataflow` and then runs those steps.

## Transform data

The Data Prep SDK offers numerous methods to help with transforming or wrangling data. These include functions that simplify adding columns, filtering out unwanted rows or columns, and imputing missing values. Transformation is about reshaping raw data into a form that can be more quickly and accurately analyzed.

## Write data

The Data Prep SDK enables writing data out at any point in a Dataflow. These writes are added as steps to the resulting Dataflow and will be executed every time the Dataflow is executed. Since there are no limitations to how many write steps there are in a pipeline, this makes it easy to write out intermediate results for troubleshooting or to be picked up by other pipelines.