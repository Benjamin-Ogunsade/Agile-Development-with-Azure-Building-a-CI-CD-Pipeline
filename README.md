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

![image](https://user-images.githubusercontent.com/28298236/209792103-2dd38240-aa6c-47c0-9333-6dbf99792fcb.png)

The above command generates the public key which is recovered via:

````
cat /home/odl_user/.ssh/id_rsa.pub
````
![image](https://user-images.githubusercontent.com/28298236/209792190-f43a95f4-c314-47cb-be8f-95d2ed3581dc.png)

This is copied and pasted [here](https://github.com/settings/keys), select "New SSH key", give it a suitable title e.g "Project2_SSH-keys". Validate it.
<img width="332" alt="image" src="https://user-images.githubusercontent.com/28298236/209792004-39f829aa-41fb-4fb7-ba05-7ea13a79cb15.png">

Hence, the git clone command will run, unhindered.

````
git clone git@github.com:Benjamin-Ogunsade/Project2.git
````
3. Below is a screenshot of the successful cloning

<img width="518" alt="image" src="https://user-images.githubusercontent.com/28298236/209791607-2f8b7f5c-307e-4968-8535-904a253857b7.png">


### Project Scaffolding
1. Create the Makefile

![image](https://user-images.githubusercontent.com/28298236/209795035-14021c84-74a6-43eb-8614-1f69a92845cf.png)

2. Create the requirements.txt file

![image](https://user-images.githubusercontent.com/28298236/209795136-61abfaa4-4684-4159-bad8-2aa0b1242038.png)

3. Create the Python virtual environment

### Create the Python Virtual Environment

````
python3 -m venv ~/.myrepo
````
![image](https://user-images.githubusercontent.com/28298236/209793932-f8f6cd47-a409-4298-a49c-2a14483b76e3.png)

````
source ~/.myrepo/bin/activate
````
![image](https://user-images.githubusercontent.com/28298236/209794012-b651ac0d-b560-490a-a17c-04694d0e8a3e.png)

Having created the vitual environment and sourced into it


4. Create the project script and file test

The project script

![image](https://user-images.githubusercontent.com/28298236/209796259-f3470cf9-87b3-4922-908a-1567251cc1e3.png)


The file test

![image](https://user-images.githubusercontent.com/28298236/209795394-707ba9cb-cf70-4e33-9861-71e17f4dccf7.png)


### Local Tests
1. To run the make all command locally:

Now that you are in the virtual environment named .myrepo, please navigate to the local cloned repo Project2.

There run the below command
````
make all
````

An error was encounter upon the first run of the make all command, this was resolved by navigating into the right directory- the local cloned repo Project2 within the virtual environment, see the image below.

![image](https://user-images.githubusercontent.com/28298236/209798761-29fb051c-4639-42d9-9733-03eb2132f265.png)

The result of the make all command ran locally is:

![image](https://user-images.githubusercontent.com/28298236/209798538-5dcc6c8e-0a5d-403d-bcfa-b84bf55de259.png)

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

![image](https://user-images.githubusercontent.com/28298236/210013283-8a6f2adf-c8fd-4bc8-92dd-65f05bfb7f4e.png)

Next, the local prediction is obtained upon running the make_prediction.sh in another cloud session/environment.

````
./make_prediction.sh
````

Ensure that the above file is earlier granted the 'execution' permission, by the use of the command:

````
chmod +x ./make_prediction.sh
````
Also, the app.py must be running before the prediction is locally executed. Below is the result of the local prediction:

![image](https://user-images.githubusercontent.com/28298236/210015299-72dd7a06-859e-4799-9cf1-4be0bb1fb960.png)

Next is to run the remote prediction, there is the need to first deploy the web app

````
az webapp up --name myflaskmlwebappy --resource-group Azuredevops --runtime "PYTHON:3.7"
````

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

The Build was successful

![image](https://user-images.githubusercontent.com/28298236/209801830-c3dbd8c6-b44c-4c94-9fbc-9f43c1400215.png)


## Continuous Delivery on Azure
Get Flask Starter [Code](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code) on the local machine

The folder was cloned and then moved to the project directory

![image](https://user-images.githubusercontent.com/28298236/209822178-9d0ac6e2-a476-4a68-8156-fc3cd37d02b0.png)


Azure Continuous Delivery PAAS 

1. The scaffolding code is replaced with Flask Machine Learning code.

2. Authorize Azure App services

* Go to Azure DevOps organizations

![image](https://user-images.githubusercontent.com/28298236/209810221-ab39f290-82d6-4989-a947-e22ec8d6ac69.png)


Producing

![image](https://user-images.githubusercontent.com/28298236/209810726-2d10b6e9-4244-43eb-82cb-ad657a8aab80.png)


* To [create](https://learn.microsoft.com/fr-fr/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl#create-an-azure-devops-project-and-connect-to-azure) a new Project on Azure DevOps named "Project 2__ Continuous Delivery on Azure" :

![image](https://user-images.githubusercontent.com/28298236/209811430-5d02bfe6-6625-4481-a8df-4de31eca27a3.png)

The new project is now created, within which the Pipeline will be implemented 

![image](https://user-images.githubusercontent.com/28298236/209811951-dc5136ec-5d37-4b1e-a246-0fcf26c53a9f.png)


* To create a [pipeline](https://learn.microsoft.com/fr-fr/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops&WT.mc_id=udacity_learn-wwl#create-a-python-specific-pipeline-to-deploy-to-app-service)

![image](https://user-images.githubusercontent.com/28298236/209812244-69f20dc8-9894-4b13-a3b9-0ad752f3eef6.png)

* Configuring the Pipeline

On the Configure tab, "Python to Linux Web App on Azure" was selected

![image](https://user-images.githubusercontent.com/28298236/209816945-2d652305-b73a-462d-85b5-4308dcefa4d9.png)

* Creating a new service connection called the "Azure Resource manager"

![image](https://user-images.githubusercontent.com/28298236/209817880-aca3e8d8-8f14-4673-a54b-ba5dbb822af1.png)


![image](https://user-images.githubusercontent.com/28298236/209821278-7f637cf0-505d-4048-aac3-df2f2893db01.png)


