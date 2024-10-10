This is a scaffolding project to create a new *devcontainer* environment for a Python application in VS Code

## Assumptions
This is an opiniated piece of work that. It assumes VS Code development on windows using WSL 2
You will get ruff and pytest as part of the project
Some VS Code settings are supplied
Even though working in a docker environment, still a virtual environment is created for the code.

## Getting started
To get started:
    1. Make sure you have the dev containers extension is VS Code installed.
    2. Clone this repo
    3. Change the name of the directory src/app to whatever package you want to use. Also change:
        - the name app in packages in pyproject.toml
        NOTE: the name of the workspaceFolder in the devcontainer.json should NOT be updated
    4. Update the pyproject.toml dependencies to whatever you need. Consider if you want to remove poetry.lock from the .gitignore
    5. Add your code
    6. Add or update the azure pipeline (or replace with a github one)
    7. Review the .dockerignore and .gitignore files
    8. Update the Readme under app/src

