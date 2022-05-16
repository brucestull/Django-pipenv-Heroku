# 02 - Create Django Project

## Resources and Links:
* [README.md](../README.md)  
* [How to start a Django project - PDXCG Style](https://github.com/PdxCodeGuild/class_otter/blob/main/3%20Django/docs/Django%20Project%20Setup.md)  

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


