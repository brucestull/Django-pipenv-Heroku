# Deploy to Heroku

## Resources:
* [Configure Django for Production](https://thinkster.io/tutorials/configuring-django-settings-for-production)

## Process:

1. Create value for `SECRET_KEY` and save as local environment variable:  
`python manage.py shell`
`from django.core.management.utils import get_random_secret_key`
`print(get_random_secret_key())`

1. Create `this_specific_project/settings` directory:  
`mkdir settings`

1. Move `this_specific_project/settings.py` to `this_specific_project/settings/common.py`.

1. Create `this_specific_project/settings/development.py` and `this_specific_project/settings/production.py`:  
    `this_specific_project/settings/development.py`:  
    ```
        from this_specific_project.settings.common import *

        DEBUG=True
    ```
    `this_specific_project/settings/production.py`:  
    ```
        from this_specific_project.settings.common import *

        DEBUG=False
    ```

1. Remove `DEBUG` from `this_specific_project/settings/common.py`.

1. Modify `BASE_DIR` in `this_specific_project/settings/common.py` since we nested `common.py` one directory down:  
    ```
    BASE_DIR = Path(__file__).resolve().parent.parent.parent
    ```

1. Modify `this_specific_project/settings/common.py`:
    ```
    import os

    SECRET_KEY = os.environ.get('SECRET_KEY')
    ```

1. Modify `this_specific_project/wsgi.py`:  
    ```
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'this_specific_project.settings.development')
    ```

1. Modify `manage.py`:  
    ```
    def main():
        ...
        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'this_specific_project.settings.development')
        ...
    ```

1. Test local server:  
`python manage.py runserver 8030`
http://localhost:8030/
http://localhost:8030/admin/

1. Log in to Heroku:  
`heroku login`

1. Create Heroku application:  
`heroku create django-pipenv-heroku`

1. Note production server and git repo addresses:  
`https://django-pipenv-heroku.herokuapp.com/`
`https://git.heroku.com/django-pipenv-heroku.git`

1. Verify remote git servers:  
`git remote -v`
    ```
    heroku  https://git.heroku.com/django-pipenv-heroku.git (fetch)
    heroku  https://git.heroku.com/django-pipenv-heroku.git (push)
    origin  https://github.com/brucestull/Django-pipenv-Heroku.git (fetch)
    origin  https://github.com/brucestull/Django-pipenv-Heroku.git (push)
    ```

1. Install [django-on-heroku](https://pypi.org/project/django-on-heroku/) and [gunicorn](https://pypi.org/project/gunicorn/):  
`pipenv install django-on-heroku==1.1.2 gunicorn==20.1.0`

1. Inspect contents of `Pipfile`:  
`cat Pipfile`
    ```
    [packages]
    ...
    django-on-heroku = "==1.1.2"
    gunicorn = "==20.1.0"
    ...
    ```

1. Modify `this_specific_project/settings/common.py`:  
    ```
    import django_on_heroku
    django_on_heroku.settings(locals())
    ```

1. Create `Procfile`:
    ```
    web: gunicorn this_specific_project.wsgi
    release: python manage.py migrate
    ```

1. Create `SECRET_KEY` and save value as production environment variable.
`python manage.py shell`
`from django.core.management.utils import get_random_secret_key`
`print(get_random_secret_key())`

1. Set `DJANGO_SETTINGS_MODULE` to `'this_specific_project.settings.production'` on production server. This will set up server to run the production settings since we will set a non-empty value for `DJANGO_SETTINGS_MODULE`:  
`heroku config:set DJANGO_SETTINGS_MODULE='this_specific_project.settings.production'`

1. Push changes to Heroku git repo:  
`git push heroku main`

1. Verify production `DEBUG` value `False`:  
`heroku login`
`heroku run python manage.py shell`
`from django.conf import settings as s`
`print(s.DEBUG)`

1. Create superuser:  
`heroku run python manage.py createsuperuser`

1. Check deployed application Admin Page:  
`https://django-pipenv-heroku.herokuapp.com/admin`
