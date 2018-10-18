# Setup

Follow instructions below to login to IBM Watson Studio.

## Download the contents of the Github repository

- Go to the main page for this [repository](https://github.ibm.com/dpape/cascon2018)
- Download the entire repository for this workshop by clicking the "Clone or Download" button and then choosing Download Zip
- Save the zip file to your local computer and then unzip it to a known location such as C:\WatsonStudioWorkshop or a location in your Documents folder if using a Mac
- Future steps in this lab will refer to <download_location> and the relative path for any files needed

## Log in to IBM Watson Studio

- Launch a new browser window and navigate to [IBM Watson Studio](https://dataplatform.cloud.ibm.com).
- Click Log in and specify your IBM ID and password for use on IBM Cloud (formerly Bluemix).
- Follow any instructions for linking your IBM Cloud Account with IBM Watson Studio.

## Setting up IBM Watson Studio and creating a new project

We will create a new project in IBM Watson Studio which will hold all the various assets used in this lab.  
Follow these steps to set up your IBM Cloud account for Watson Studio.

- First, browse the [Watson Services](https://console.bluemix.net/developer/watson/services) or alternatively you can click on the hamburger menu at the top left, click Watson and then click Browse all Watson services.

![Browse Watson Services][setup-image-1]
- Choose the Watson Studio service.  On the creation page give it a name, choose a region (US South) and choose the Lite plan.  Click Create to create the service.

![Create Watson Service][setup-image-2]
- After the service is created, click Get Started in order to launch Watson Studio.
- Under Recently updated projects, click on New Project.
- Choose "Complete Project" in order to have access to the entire suite of tools in IBM Watson Studio and then click OK.

![Create New Project][setup-image-3]
- Give your new project a name.  For example: "watson-studio-cascon-2018" and give it an optional description.

![Create New Project 2][setup-image-4]

- Choose an existing storage service or else click Add to create a new one.  (If you create a new storage service you can use the free Lite plan.  Choose a region and complete the overlay to create the storage service).

- Next we're going to create and associate an Apache Spark service for use in the lab.  Apache Spark is an open-source computing framework that allows fast execution of workloads like machine learning and SQL.  We'll be using Spark from within a Jupyter notebook to process our workloads.  

- From the project Overview page, click on Settings.  Under Associated Services click on Add Service and choose Spark.  Choose the Lite (free) plan and then on the subsequent overlay specify a name and region (US South) for the service.  Click Create to finalize creation of the service. 

Now the initial setup is complete.  Explore the IBM Watson Studio Dashboard!  There are tabs for project overview, assets, settings and more.  Spend a few minutes getting familiar with the user interface.  IBM Watson Studio is tightly integrated with IBM Cloud.

You can navigate to IBM Watson Studio from IBM Cloud by using the top left hand navigation.

[comment]: # "------------------------------------------------------------------------------"
[comment]: # "                              Links / Reference                               "
[comment]: # "------------------------------------------------------------------------------"

[setup-image-1]: images/Browse_Watson_Services.png "Browse Watson Services"
[setup-image-2]: images/Create_Watson_Service.png "Create Watson Service"
[setup-image-3]: images/Create_New_Project.png "Create New Project"
[setup-image-4]: images/Create_New_Project_2.png "Create New Project 2"


