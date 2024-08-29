# Django
## Django::Configuration Steps

The project name for our purposes has been defined as ERS(Exam-Room-Allocation)
System. The application name for this puporse will be ERS-App

``` 
!pip install django
!pip install djangorestframework.jsonapi
!pip install python-dotenv

!django-admin startproject {project_name}

%cd {project_name}

!python manage.py startapp {app_name}

%cd {app_name}
```

## Django:: Rewritting Views.py

```
%%writefile views.py
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello World")
```

## Django:: Deployment Steps

For our deploement purposes, we are utilizing a free open-source resource called
ngrok. The documentation link has been provided for ngrok above. We are tunelling
our website through the free-key that will be generated in ngrok dashboard. For all
purposes, the port that we will be tunelling is 7000

```
!pip install pyngrok --quiet

from pyngrok import ngrok

ngrok.kill()

auth_token=""
ngrok.set_auth_token({auth_token})

%cd /content/{project_name}

!python manage.py migrate
!python manage.py runserver {port}

ngrok.kill()
```
