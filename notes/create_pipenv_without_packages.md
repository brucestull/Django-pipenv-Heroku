# Create `pipenv` virtual environment without installing new packages

## Resources and Links:
* [README.md](../README.md)  
* [Pipenv & Virtual Environments - python-guide.org](https://docs.python-guide.org/dev/virtualenvs/)  
* [Pipenv: A Guide to the New Python Packaging Tool - realpython.com](https://realpython.com/pipenv-guide/)  

## Assumptions:  
* User has `pipenv` installed globally.  

## Process:

1. Ensure current directory is root directory of repository or project.

1. Inspect current directory structure:
`tree /f /a`
    ```
    C:.
    |   .gitignore
    |   README.md
    |
    \---.vscode
    ```

1. *(ACTION)* Create `pipenv`:
`pipenv install`

1. Note virtual environment location:  
`C:\Users\Bruce\.virtualenvs\Django-pipenv-Heroku-[unique code]`  
`C:\Users\User\.virtualenvs\Django-pipenv-Heroku-[unique code]`  

1. (ACTION) Set Python interpreter:  
View >> Command Palette >> Python: Select Interpreter >> Select at workspace level >> ...  
`C:\Users\User\.virtualenvs\Django-pipenv-Heroku-[unique code]\Scripts\activate.ps1`  

1. Inspect new directory structure:
    * NOTE: We now have two new files: `Pipfile` and `Pipfile.lock`. These are created automatically when we run `pipenv install`. The `Pipfile` file is used to prescribe dependencies.
`tree /f /a`
    ```
    C:.
    |   .gitignore
    |   Pipfile
    |   Pipfile.lock
    |   README.md
    |   
    \---.vscode
    ```

1. Inspect contents of `Pipfile`:
* NOTE: `packages` doesn't show any packages since we haven't specified any yet.
`cat Pipfile`
    ```
    [[source]]
    url = "https://pypi.org/simple"
    verify_ssl = true
    name = "pypi"

    [packages]

    [dev-packages]

    [requires]
    python_version = "3.10"
    ```

1. (ACTION) Activate virtual environment:  
    * NOTE: This only needs to be done if terminal isn't already using virtual environment.
`pipenv shell`  

1. Inspect packages installed in virtual environment:  
`pip list`  
    ```
    Package    Version
    ---------- -------
    pip        22.0.4
    setuptools 62.1.0
    wheel      0.37.1
    ```


