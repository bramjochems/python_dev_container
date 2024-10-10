This is a scaffolding project to create a new *devcontainer* environment for a Python application in VS Code

## Purpose
This project provides a pre-configured development environment (DevContainer) for Python applications in Visual Studio Code.

## Assumptions:
- You're using Windows with WSL 2.
- You'll need VS Code with the Dev Containers extension installed.
- You'll use Python's pyproject.toml for package management.
- You'll leverage Azure Pipelinesfor CI/CD

## Getting started
To get started:
1. Make sure you have the __Dev Containers extension__ in VS Code installed.
2. __Clone__ this repo
    ```
    git clone https://dev.azure.com/riskatwork/Scaffolding/_git/PythonDevcontainer
    ```
3. __Customize settings__:
    - __Rename__ ```src/app``: Change the directory name ot match your projects name. Also update:

    - __Update__ the ```pyproject.toml```: Modify the ```name``` and ```packages``` fields to reflect your project's details. NOTE: the name of the workspaceFolder in the devcontainer.json and the application directory in the DockerFile should not be changed.
    - __Adjust dependencies__: Update your ```pyproject.toml``` with the dependencies you need.


4. __Review project files__:
    - __Configure CI/CD__: Update or replcate the existing azure pipeline to suit your requirements
    - Update the ```README.md```
    - Examine the ```.dockerignore``` and ```.gitignore``` files to ensure they're appropriate for you

5. __Write your code__: Create your python files within the ```src``` directory


