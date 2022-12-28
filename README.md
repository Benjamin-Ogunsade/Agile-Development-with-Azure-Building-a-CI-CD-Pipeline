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

1. Enable Github Actions
Go to your Github Account and enable Github Actions.

![image](https://user-images.githubusercontent.com/28298236/209800174-fedbf5e0-6e0c-4c48-b808-f5234f237f89.png)

GitHub Actions is enabled and the a workflow name "Python application test with Github Actions" was created:

![image](https://user-images.githubusercontent.com/28298236/209800479-a71f95ca-0884-4fe9-81ab-7519a58d4fb1.png)

2. Replace yml code
The pythonapp.yml code was replaced


