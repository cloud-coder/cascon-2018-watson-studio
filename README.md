# CASCON Watson Studio Lab

## Table of Contents

* [Overview](#overview)
* [Setup](#setup)
* [Data Set Analysis Using Jupyter Notebook](#data-set-analysis-using-jupyter-notebook)
* [Data Set Analysis Using IBM Watson Studio](#data-set-analysis-using-watson-studio)
* [Conclusion](#conclusion)

## Overview

More than ever before, larger and more comprehensive data sets are being made publicly available on the internet. You can find data on all sorts of topic such as housing prices, sports data, wine reviews, weather, movies, TV shows, gun violence and anything you can think of.  

The low cost of storage has also enabled companies to collect and maintain a variety of business data, both structured and unstructured.  Extracting insights from the mix of publicly available data and private business data is crucial to determining the direction of a business and maintaining an edge on competitors.  Companies can now analyze such data to augment their decision making process with fact based observations. Additionally, with further maturity, they are able to apply predictive analytics and leverage machine learning to make more informed decisions and plans.

Working with and analyzing such large data sets can be overwhelming.  How does one make sense of all this data, and potentially combine different data sets to get new insights for business needs?  How do domain experts, data engineers, data scientists and developers work together towards a common goal?

IBM Watson Studio is the newest suite of data science tools offered by IBM and has evolved from IBM Data Science Experience (DSX).  It provides a suite of tools geared towards both application developers and data scientists which can help make sense of the data.  IBM Watson Studio provides tooling for importing, refining, visualizing and interpreting data.  IBM Watson Studio can be used by those who do not have a development background thus providing a rich platform for data science without necessarily knowing the finer details.

Built on IBM Cloud, IBM Watson Studio also provides Jupyter Notebooks using Scala, R or Python.  A notebook can utilize an Apache Spark engine to perform direct tasks that perhaps a data scientist or programmer might be more familiar with.  IBM Watson Studio allows domain experts and data experts to use the same platform to collaborate on a data science project. 

## Setup

Follow instructions in [setup section](01-setup/setup.md) to sign in to IBM Cloud and set up your account.  You can use a trial account for this purpose.

## Data Set Analysis Using Jupyter Notebook

[This section](02-data-set-analysis-jupyter/data-set-analysis-jupyter.md) will use a Jupyter notebook and walk you through:
* Importing a data set with Pixiedust
*	Data Frame Creation, Analysis and Refinery using Pixiedust
*	Data Visualization (charts) using Pixiedust

## Data Set Analysis Using IBM Watson Studio

[This section](03-data-set-analysis-ws/data-set-analysis-ws.md) will use IBM Watson Studio to walk you through:
* Importing a data set with IBM Watson Studio
*	Viewing and Refining Data within IBM Watson Studio
*	Data Visualization (charts) using Cognos Embedded Dashboards
*	Sharing Dashboards

## Conclusion

In this lab you have learned some of the interesting features and tools in IBM Watson Studio that can be used for data visualization.  We showed how to refine and visualize data using a Jupyter Notebook and Python, which would be geared towards more technical users or data scientists.  We also showed how many of the same refinements and visualizations can be made using Cognos Embedded  Dashboards, which might be more interesting to non technical users or analysts.  

The labs only touched on a few parts of IBM Watson Studio.  Now that you know some basics you are encouraged to explore on your own!  Thank you for attending!

