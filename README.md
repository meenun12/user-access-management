# Flask User Access Management System

This is a simple Flask web application that allows product owners to manage teams and employees, and assign permissions to view teams dashboard.
Here is also a loom video, which explains how to install and use this app
https://www.loom.com/share/3a78c0e472e84c87926980c3d6e3e98d


## Installation

1. Clone the repository to your local machine.
2. Create a virtual environment using your preferred tool, 
   1. I used here poetry, for that you would have to install first poetry

   ```bash
   pip3 install poetry
   poetry --version
   ```
   
   If installation successful than run following command to go to poetry shell
   ```bash
   poetry shell 
   ```
   
   Install the dependency using this command
   ```bash
   poetry install
   ``` 
  
   2. Other way of doing it
   ```bash
   python3 -m venv env
   source env/bin/activate 
   ```
   
   Install the dependency using this command
   ```bash
   pip3 install -r requirements.txt
   ``` 

5. Start the application by running 
   ```bash
   python3 app.py
   ```

## Usage

Once the application is running, you can access the following URLs:

- http://localhost:5004/ - Dashboard here you can see how many users are assign per team.
- http://localhost:5004/add_employee - Allows users to add a new employee.
- http://localhost:5004/add_team - Allows users to add a new team.
- http://localhost:5004/assign_team - Allows Product Owners to grant permissions to employees to view team dashboards.

## Dependencies

This application was developed using the following technologies:

- Flask
- Sqlite3
- Flask WTF
- Jinja2

## Note

1. In case of any issue with DB, you can create it in following way also
```bash
export FLASK_APP=app
flask shell
from app import db, Team, Employee
db.create_all()
```

2. How to access the database
- Open the command prompt on your computer.
- Navigate to the directory where your SQLite database file is located using the cd command.
- Type sqlite3 followed by the name of your database file and press Enter.
- For example, if your database file is named user_access_management.db, you would type 
```bash
sqlite3 user_access_management.db
```

## Deploying a Flask App using Azure Artifacts and Pipelines

Here are general steps for deploying a Flask app using Azure Artifacts and Pipelines. 

## Prerequisites
- Azure subscription
- Azure DevOps organization or project
- Basic knowledge of Azure Artifacts and Pipelines
- Flask app code and dependencies
# Steps
1. I will create an Azure Artifacts feed to store application artifacts, such as Flask app code and dependencies.
   1. In the Azure portal, I have to navigate to DevOps organization or project.
   2. Under "Artifacts", select "New feed".
   3. I will Choose a name and other settings for feed, and then select "Create". 
2. Create an Azure Pipeline to build and deploy your Flask app.
   1. In the Azure portal, navigate to DevOps organization or project.
   2. Under "Pipelines", select "New pipeline".
   3. Then I will choose a repository and branch for pipeline, and then select "Continue".
   4. After that I will choose a template for pipeline, such as "Python to Linux Web App on Azure", and then select "Apply".
   5. Configure the pipeline settings, such as your Azure subscription and resource group, and then select "Save and run".
   6. After that build a Docker image using your Dockerfile.
3. Configure pipeline:
   1. In pipeline settings, under "Tasks", edit the tasks for your pipeline as needed.
   2. For example, I need to add a task to retrieve application artifacts from the Azure Artifacts feed, or install any dependencies.
   3. I also need to configure pipeline to build and package Flask app, such as by running pip3 install -r requirements.txt and python setup.py sdist. 
4. Deploying User Access Management app 
   1. Once pipeline is configured, save and run it to build and deploy app.
   2. Flask app will be deployed to an Azure App Service, such as an Azure Web App or Azure Functions app.
   3. After that I will monitor the progress of deployment in the Azure portal or in the DevOps dashboard
#
 
