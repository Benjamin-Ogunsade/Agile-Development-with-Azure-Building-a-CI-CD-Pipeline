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

![image](https://user-images.githubusercontent.com/28298236/210118974-be95c266-28e5-4d4a-99be-ed86d75438f0.png)


In the previously executed command, it is expedient to state the right -rg which is the -rg on the Azure portal of your Az subscription.

The app is now on the fly and publicly acccessibly via the URL (https://myflaskmlwebapp.azurewebsites.net/) provided in the result provided; the next image depicts the rendition of the URL.



Delete next
![image](https://user-images.githubusercontent.com/28298236/210018521-1210f0ca-f342-4918-b07b-637205d9aeec.png)

The URL is now recovered and inserted in the make_predict_azure_app.sh, specifically in the POST url.

The app app.py must keep on runnning in the second cloud shell environment.

Thereafter, the make_predict_azure_app.sh is executed using:

````
./make_predict_azure_app.sh
````

Produces the result:

![image](https://user-images.githubusercontent.com/28298236/210019418-ada9491e-3b83-4e8c-be0f-6b3ba65be3a0.png)

The result shows that the app runs on the port 443.

Next, we head to the Azure portal to located the deployed App Service Plan and the App Service.

![image](https://user-images.githubusercontent.com/28298236/210019835-a17973cd-d65c-4e0f-b4b8-f2e62281656f.png)

Inasmuch as the App Service is running, the URL will be accessible.

To generate the log, the following command is executed:

````
az webapp log tail
````

The following result is produced:

![image](https://user-images.githubusercontent.com/28298236/210020406-43833d19-0897-49ed-be0d-abe153b47d2a.png)

From the above result, it is evident that

* Container myflaskmlwebappy_0_5e53f50d for site myflaskmlwebappy initialized successfully and is ready to serve requests.


In order to check the performance validation using the locustfile.py file, the prediction parameters are correlated with that of the app.py file.

Next, the file is run

````
locust -f locustfile.py --headless -u 20 -r 5 -t 20s
````

![image](https://user-images.githubusercontent.com/28298236/210023306-ec728d4c-0c19-401d-a288-0d8bdde11455.png)

The result is :

![image](https://user-images.githubusercontent.com/28298236/210023367-d4a1db2d-11a7-4480-bf74-b507ee357e0c.png)

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

![image](https://user-images.githubusercontent.com/28298236/210109394-b86ded61-47f2-48a8-86ae-eb048c1df2ea.png)

In summary for the Cloud share, the local and remote predictions are working correctly.

* Next, proceed to the Azure Portal to launch the "Azure DevOps Organization" 



### Azure Continuous Delivery PAAS 

As a means of recapitulation,

1. The scaffolding code has been replaced with Flask Machine Learning code.

2. The Azure App services has been authorized and our deployed app is currently running on our instance on the Azure platform.

* Go to Azure DevOps organizations

![image](https://user-images.githubusercontent.com/28298236/209810221-ab39f290-82d6-4989-a947-e22ec8d6ac69.png)


Producing

![image](https://user-images.githubusercontent.com/28298236/209810726-2d10b6e9-4244-43eb-82cb-ad657a8aab80.png)


* To [create](https://learn.microsoft.com/fr-fr/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl#create-an-azure-devops-project-and-connect-to-azure) a new Project on Azure DevOps named "Project 2__ Continuous Delivery on Azure" :

![image](https://user-images.githubusercontent.com/28298236/209811430-5d02bfe6-6625-4481-a8df-4de31eca27a3.png)

The new project is now created, within which the Pipeline will be implemented 

![image](https://user-images.githubusercontent.com/28298236/209811951-dc5136ec-5d37-4b1e-a246-0fcf26c53a9f.png)






We configure the Pipeline before creating one:

* Configuring the Pipeline

Click 'Project Settings' --> Service Connections

On the Configure tab, "Python to Linux Web App on Azure" was selected

![image](https://user-images.githubusercontent.com/28298236/209816945-2d652305-b73a-462d-85b5-4308dcefa4d9.png)


* Creating a new service connection called the "Azure Resource manager"

Click 'Create service connection'

![image](https://user-images.githubusercontent.com/28298236/209817880-aca3e8d8-8f14-4673-a54b-ba5dbb822af1.png)

Choose 'Azure Resource Manager' 

![image](https://user-images.githubusercontent.com/28298236/209821278-7f637cf0-505d-4048-aac3-df2f2893db01.png)

Choose 'Service principal (automatic) as authentication method, in order to enable the Build run automatically upon modification of the artifact.

Make the following choices to create a "New Azure service connection"

* Scope level:  'Subscription'
* Subscription:  select your Azure subscription
* Resource group:  select the resouce group of the earlier Azure deployed app 
* Service connection: "project2_serv_cxn"

Ensure to check in 'Grant access permission to all pipelines'

Once





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

