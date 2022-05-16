# 01 - Create `pipenv` virtual environment

## Process:
1. Inspect current directory structure:  
`tree . /f /a`  
    ```
    DJANGO-PIPENV-HEROKU
    |   .gitignore
    |   README.md
    |
    \---.vscode
    ```

1. Inspect currently installed packages:  
`pip list`  
    ```
    Package            Version
    ------------------ ---------
    pip                22.0.4
    pipenv             2022.1.8
    ```

1. Inspect installed python version:  
`python -V`  
    ```
    Python 3.10.3
    ```

1. (ACTION) Create `pipenv` virtual environment:  
`pipenv install`  

1. Note virtual environment location:  
`C:\Users\Bruce\.virtualenvs\Django-pipenv-Heroku-[unique code]`  
`C:\Users\User\.virtualenvs\Django-pipenv-Heroku-[unique code]`  

1. (ACTION) Set Python interpreter:  
View >> Command Palette >> Python: Select Interpreter >> Select at workspace level >> ...
`C:\Users\User\.virtualenvs\Django-pipenv-Heroku-[unique code]\Scripts\activate.ps1`  

1. (ACTION) Activate virtual environment:  
`pipenv shell`  

1. Inspect current directory structure. Note addition of `Pipfile` and `Pipfile.lock`:  
`tree . /f /a`  
    ```
    DJANGO-PIPENV-HEROKU
    |   .gitignore
    |   Pipfile
    |   Pipfile.lock
    |   README.md
    |
    \---.vscode
    ```

1. Inspect contents of `Pipfile`:  
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

1. Inspect packages installed in virtual environment:  
`pip list`  
    ```
    Package    Version
    ---------- -------
    pip        22.0.4
    setuptools 62.1.0
    wheel      0.37.1
    ```

1. (ACTION) Install Django:  
`pipenv install django`  

1. Inspect packages installed in virtual environment:  
`pip list`  
    ```
    Package    Version
    ---------- -------
    ...
    Django     4.0.4
    ...
    ```

1. Inspect contents of `Pipfile`. NOTE: Django version isn't specified:  
`cat Pipfile`  
    ```
    ...
    [packages]
    ...
    django = "*"
    ...
    ```

1. (ACTION) Install specific Django version:  
`pipenv install django==4.0`  

1. Inspect packages installed in virtual environment:  
`pip list`
    ```
    Package    Version
    ---------- -------
    ...
    Django     4.0
    ...
    ```

1. Inspect contents of `Pipfile` NOTE: Django version is now specified:  
`cat Pipfile`  
    ```
    ...
    [packages]
    ...
    django = "==4.0"
    ...
    ```
