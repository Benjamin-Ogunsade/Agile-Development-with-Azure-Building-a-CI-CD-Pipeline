# Project2
Udacity Project 2



[![Python application test with Github Actions](https://github.com/Benjamin-Ogunsade/Project2/actions/workflows/pythonapp.yml/badge.svg)](https://github.com/Benjamin-Ogunsade/Project2/actions/workflows/pythonapp.yml)


Here is the link to my Project Plan using Spreadsheet: https://testfutaedu-my.sharepoint.com/:x:/g/personal/baogunsade_futa_edu_ng/Eexutlf_95xLrofbrLEFyTgB3uSsO1NEl-QEsq2Hgl06Cg?e=Taa0TJ

Here is an preview of it:
![image](https://user-images.githubusercontent.com/28298236/209764558-6246a9e6-9459-49f8-b9ca-b418ef8c351f.png)


Here is the link to my Trello Project : https://trello.com/b/LGEaJodJ

Below is a screenshot 
![image](https://user-images.githubusercontent.com/28298236/209764199-97fd9583-1df3-49c4-9091-ae40d2cf5ba7.png)

## CI: Set Up Azure Cloud Shell 
### Building a CI/CD Pipeline

### Dependencies
1. Create an [Azure Account](https://portal.azure.com) 
2. Install the [Azure command line interface](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

### Instructions
To clone the starter repository, a public ssh key needs to be generated for remote authentication to GitHub, via the CLI comnand

````
ssh-keygen -t rsa
````

![image](https://user-images.githubusercontent.com/28298236/210119072-fc1829a1-1483-41eb-9bcb-c3fa8224bbc1.png)


The above command generates the public key which is recovered via:

````
cat /home/odl_user/.ssh/id_rsa.pub
````

![image](https://user-images.githubusercontent.com/28298236/210119125-5f15b10b-96d3-46d2-a446-5ab84bf24445.png)


This is copied and pasted [here](https://github.com/settings/keys), select "New SSH key", give it a suitable title e.g "Project2_SSH-keys". Validate it.

<img width="332" alt="image" src="https://user-images.githubusercontent.com/28298236/209792004-39f829aa-41fb-4fb7-ba05-7ea13a79cb15.png">

Hence, the git clone command will run, unhindered.

````
git clone git@github.com:Benjamin-Ogunsade/Project2.git
````
3. Below is a screenshot of the successful cloning

<img width="512" alt="image" src="https://user-images.githubusercontent.com/28298236/210119268-2fc340d7-d3b0-4609-b98b-f2cf9f65f95c.png">

### Project Scaffolding
1. Create the Makefile

![image](https://user-images.githubusercontent.com/28298236/209795035-14021c84-74a6-43eb-8614-1f69a92845cf.png)

2. Create the requirements.txt file

![image](https://user-images.githubusercontent.com/28298236/209795136-61abfaa4-4684-4159-bad8-2aa0b1242038.png)

3. Create the Python virtual environment

### Create the Python Virtual Environment

````
python3 -m venv ~/.myrepo
source ~/.myrepo/bin/activate
````

![image](https://user-images.githubusercontent.com/28298236/210119309-230eaa45-978a-4691-906d-b22d77d2326e.png)


Having created the vitual environment and sourced into it


4. Create the project script and file test

The project script

![image](https://user-images.githubusercontent.com/28298236/209796259-f3470cf9-87b3-4922-908a-1567251cc1e3.png)


The file test

![image](https://user-images.githubusercontent.com/28298236/209795394-707ba9cb-cf70-4e33-9861-71e17f4dccf7.png)


### Local Tests
1. To run the make all command locally:

Now that you are in the virtual environment named .myrepo, please navigate to the local cloned repo Project2.

Then run the below command

````
make all
````

![image](https://user-images.githubusercontent.com/28298236/210119425-9e445f42-db15-4527-a264-375c0d8af668.png)

An error was encounter upon the first run of the make all command, this was resolved by navigating into the right directory- the locally cloned repo Project2 within the virtual environment, see the image below.

![image](https://user-images.githubusercontent.com/28298236/209798761-29fb051c-4639-42d9-9733-03eb2132f265.png)

The result of the make all command ran locally is:

![image](https://user-images.githubusercontent.com/28298236/210120369-86db7b8a-b3ba-4261-8d83-f0f973f2827b.png)


test_hello.py::test_hello_subtract PASSED                      [100%]

## CI: Configure GitHub Actions

Before going into the GitHub Actions buid proper, we need to start the application in a new cloud session, and then source into the python virtual environment ".myrepo"

````
source ~/.myrepo/bin/activate
cd Project2/
````

Next, we run "app.py" to start the application

````
python app.py
````

Before you run this command, ensure that you have the "make all" command already ran: which calls the Makefile installing all the modules or dependencies as listed in the requirements.txt file.


![image](https://user-images.githubusercontent.com/28298236/210013142-e45df605-1a67-4846-9a2b-357553fdcd9c.png)

The app is now up and running on the localhost port 5000 (127.0.0.1:5000). 

![image](https://user-images.githubusercontent.com/28298236/210120504-1cd34453-5211-4d10-ac08-7b3aec146014.png)

Next, the local prediction is obtained upon running the make_prediction.sh in another cloud session/environment.

````
./make_prediction.sh
````

Ensure that the above file is earlier granted the 'execution' permission, by the use of the command:

````
chmod +x ./make_prediction.sh
````

Also, the app.py must be running before the prediction is locally executed. Below is the result of the local prediction:

![image](https://user-images.githubusercontent.com/28298236/210120634-b2272d9e-8274-42f6-ad7d-48a5e15bfd00.png)

Next is to run the remote prediction, there is the need to first deploy the web app

````
az webapp up --name myflaskmlwebapp --resource-group omoobanimi234 --runtime "PYTHON:3.7"
````

The result produced was :

![image](https://user-images.githubusercontent.com/28298236/210121147-ead5ef66-48c2-4c77-a43f-93f65ba28fc5.png)


In the previously executed command, it is expedient to state the right -rg which is the -rg on the Azure portal of your Az subscription.

The app is now on the fly and publicly acccessibly via the URL (https://myflaskmlwebapp.azurewebsites.net/) provided in the result provided; the next image depicts the rendition of the URL.

![image](https://user-images.githubusercontent.com/28298236/210121075-001d3f40-232e-4e8c-9910-fb7a59b96bbd.png)


The URL is now recovered and inserted in the make_predict_azure_app.sh, specifically in the POST url.

The app app.py must keep on runnning in the second cloud shell environment.

Thereafter, the make_predict_azure_app.sh is executed using:

````
./make_predict_azure_app.sh
````

Produces the result:

![image](https://user-images.githubusercontent.com/28298236/210121203-12cdf716-2251-41c0-97cf-a0ab48c5c7ef.png)

The result shows that the app runs on the port 443.

Next, we head to the Azure portal to located the deployed App Service Plan and the App Service.


![image](https://user-images.githubusercontent.com/28298236/210121263-b3091805-46d0-48bd-9326-a5f63a5e37ec.png)


Inasmuch as the App Service is running, the URL will be accessible.

To generate the log, the following command is executed:

````
az webapp log tail
````

The following result is produced:

![image](https://user-images.githubusercontent.com/28298236/210121427-c29d90a8-bf62-4b40-a9a7-78823ac5e8a0.png)

From the above result, it is evident that

* Container myflaskmlwebapp_0_3e8c32b2 for site myflaskmlwebapp initialized successfully and is ready to serve requests.

In order to check the performance validation using the locustfile.py file, the prediction parameters are correlated with that of the app.py file.

Next, the file is run

````
locust -f locustfile.py --headless -u 20 -r 5 -t 20s
````

![image](https://user-images.githubusercontent.com/28298236/210121562-b3abfc23-3fc6-4e96-bfb3-230abe7dcdb5.png)

The result is :

![image](https://user-images.githubusercontent.com/28298236/210121482-ad94615c-9005-45c2-932a-560f08522fc5.png)


### CI: Configure GitHub Actions

The next phase of the project is to perform the Azure DevOps deployment using CI/CI Azure Pipeline.

* First, verify that the WebApp url is active via the command

````
./make_predict_azure_app.sh
````

And true is the case; it is still active on port 443.

* Second, verify this

````
./make_prediction.sh
````

Both works still as shown below :

![image](https://user-images.githubusercontent.com/28298236/210121727-08e2a4be-e522-43e1-a0a0-1d9f0c0b1a04.png)

There was an initial fail to connect error due to the fact that app.py was temporarily down.

In summary for the Cloud share, the local and remote predictions are working correctly.

* Next, proceed to the Azure Portal to launch the "Azure DevOps Organization" 


### Azure Continuous Delivery PAAS 

As a means of recapitulation,

1. The scaffolding code has been replaced with Flask Machine Learning code.

2. The Azure App services has been authorized and our deployed app is currently running on our instance on the Azure platform.

* Go to Azure DevOps organizations

![image](https://user-images.githubusercontent.com/28298236/210121793-83d6006f-e40a-4dac-9df9-c9bde4606b80.png)

Producing

![image](https://user-images.githubusercontent.com/28298236/210121805-d2add2cc-cfb5-4ef3-941f-1c4cd824ef27.png)

Click "My Azure DevOps Organizations"

* To [create](https://learn.microsoft.com/fr-fr/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl#create-an-azure-devops-project-and-connect-to-azure) a new Project on Azure DevOps named "My_Flask_ML_app_project2" :

* Visibility : 'Private'

The new project is now created, within which the Pipeline will be implemented 

![image](https://user-images.githubusercontent.com/28298236/210121986-7aa00cb1-d24b-4d77-8954-c46a8597db2a.png)

We configure the Pipeline before creating one:

* Configure the Pipeline

- Click 'Project Settings' --> Service Connections


* Creating a new service connection called the "Azure Resource manager"

- Click 'Create service connection'



![image](https://user-images.githubusercontent.com/28298236/209817880-aca3e8d8-8f14-4673-a54b-ba5dbb822af1.png)

- Choose 'Azure Resource Manager' 

Choose 'Service principal (automatic) as authentication method, in order to enable the Build run automatically upon modification of the artifact.

Make the following choices to create a "New Azure service connection"

* Scope level:  'Subscription'
* Subscription:  select your Azure subscription
* Resource group:  select the resouce group of the earlier Azure deployed app 
* Service connection: "project2_serv_cxn"

Ensure to check in 'Grant access permission to all pipelines'

Here is a brief re-cap in picture:

![image](https://user-images.githubusercontent.com/28298236/210122510-7d541902-6157-4129-b423-4af16e1009fe.png)

Please ensure your browser authorizes all automatic redirections to allow for the  authentification page pop-up, then select the resource group in which the app was deployed in the Azure Portal.

The service connection is finally established as depicted below:

![image](https://user-images.githubusercontent.com/28298236/210122574-1d8e76ea-10ab-41ba-823e-ab05ef7d92c1.png)


Once the service connection is established between the AzureDevOps Organization project and the Azure Portal, one can proceed to configure the CI/CD Pipeline for the python ML Flask app.




### Configure the CI/CD Pipeline for the python ML Flask app 

* Go to "Pipeline",

* Click "Create Pipeline"

* Select "GitHub (YAML)" as the YAML file will be stored on the Gitub repo

* Select the project repo stored on GitHub "project2/"

* Configure your Pipeline : "Python to Linux Web App on Azure" and select the Azure sub
 You need to sign-in here.
 
* Web App name : "myflaskmlwebapp"

Validate and configure

Automatically, the YAML file is generated and the resources are configured, including the service connection details containing all the information necessary for its CI/CD functionalities.

Next,

* "save and run"

On run, it proceeds to the Build stage and Deploy stage.





  


![image](https://user-images.githubusercontent.com/28298236/209816945-2d652305-b73a-462d-85b5-4308dcefa4d9.png)







* To create a [pipeline](https://learn.microsoft.com/fr-fr/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl#create-a-python-specific-pipeline-to-deploy-to-app-service)

![image](https://user-images.githubusercontent.com/28298236/209812244-69f20dc8-9894-4b13-a3b9-0ad752f3eef6.png)







1. Enable Github Actions

Go to your Github Account and enable Github Actions.

![image](https://user-images.githubusercontent.com/28298236/209800174-fedbf5e0-6e0c-4c48-b808-f5234f237f89.png)

GitHub Actions is enabled and the a workflow name "Python application test with Github Actions" was created:

![image](https://user-images.githubusercontent.com/28298236/209800479-a71f95ca-0884-4fe9-81ab-7519a58d4fb1.png)

2. Replace yml code

The pythonapp.yml code was [replaced](https://github.com/Benjamin-Ogunsade/Project2/blob/main/.github/workflows/pythonapp.yml)

![image](https://user-images.githubusercontent.com/28298236/209801198-2bbbe2e4-18e8-49cb-807b-58ce90214439.png)

3. Verify Remote Tests pass

The changes are push-ed to GitHub and both lint and test steps were verifed which passed test.

Below is a screenshot of the passed GitHub Actions build

![image](https://user-images.githubusercontent.com/28298236/209801334-5eb6a45d-bcd2-49d8-88d9-a6cae5ccf469.png)

The Build was successfull

![image](https://user-images.githubusercontent.com/28298236/209801830-c3dbd8c6-b44c-4c94-9fbc-9f43c1400215.png)


## Continuous Delivery on Azure
Get Flask Starter [Code](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code) on the local machine

The folder was cloned and then moved to the project directory

![image](https://user-images.githubusercontent.com/28298236/209822178-9d0ac6e2-a476-4a68-8156-fc3cd37d02b0.png)

