# 02 - Create Django Project

## Resources:

## Process:

1. Create Django Project:  
`django-admin startproject this_specific_project .`

1. Check for Green Rocket:  
`python manage.py runserver 8030`
http://localhost:8030/

1. Stop server.
`Ctrl+C`

1. Perform migrations. NOTE: When using a CustomUser, run migrations on CustomUser model's app before other apps:
`python manage.py migrate`

1. Create superuser:  
`python manage.py createsuperuser`

1. Test server admin and homepage:  
`python manage.py runserver 8030`
http://localhost:8030/
http://localhost:8030/admin/


