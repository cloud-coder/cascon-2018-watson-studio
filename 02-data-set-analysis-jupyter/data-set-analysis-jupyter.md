# Data Set Analysis with Jupyter Notebooks

## Log in to IBM Watson Studio

- Launch a new browser window and navigate to [IBM Watson Studio](https://dataplatform.cloud.ibm.com).
- Click Log in and specify your IBM ID and password for use on IBM Cloud (formerly Bluemix).

## Creating a Jupyter Notebook

Within the IBM Watson Studio project, navigate to the Assets tab.  You'll see various types of Assets that can be created within an IBM Watson Studio project such as Models, Dashboards and Notebooks.

We will be creating a new Notebook and using it to import, refine and visualize some data from within the IBM Watson Studio project.  For the purpose of this lab, the notebook has already been created.  We'll be importing it and executing the individual steps in order demonstrate the functionality.

- Navigate to Assets > Notebooks and click the New Notebook link
- On the New Notebook page choose "From File".  Click the "Choose File" button and specify the Notebook File as <download_location>/cascon-2018-watson-studio-master/02-data-set-analysis-jupyter/visualizing-data.ipynb.

- In the Select Runtime section, select the Spark Service that was created in the Setup portion of the lab (example spark-cascon2018-dpape).
- Give the Notebook a name such as "Visualizing Data with Notebooks" and optional Description and click Create Notebook. 
![Create Notebook][notebook-image-1]

- Wait for a few seconds while the Notebook is created and the Kernel is started.

- The rest of the instructions for this lab are contained within the Notebook itself.  Continue in the Notebook to complete the lab.

[comment]: # "------------------------------------------------------------------------------"
[comment]: # "                              Links / Reference                               "
[comment]: # "------------------------------------------------------------------------------"

[notebook-image-1]: images/Create-Notebook.png "Create Notebook"
