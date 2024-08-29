# Django::Configuration Steps

``` 
!pip install django
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
