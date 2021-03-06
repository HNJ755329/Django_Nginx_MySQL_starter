# Django_Nginx_MySQL_starter
You can start easily Django + Nginx + MySQL on your Local and Server(VPS) with docker.


## Requirement
This starter kit is require docker and docker-compose.
### Install docker and docker-compose
You should install docker and docker-compose.
- docker  
https://docs.docker.com/install/linux/docker-ce/ubuntu/
- docker-compsoe
```console
$ sudo apt install -y docker-compose
```
## Usage

First of all, you create django project.
```console
$ docker-compose run python django-admin.py startproject app .
```

### Prepare Migrations
Django default sql is sqlite.
So before migration command, you fix /src/app/settings.py

```Python:settings.py
"""
Django settings for app project.

Generated by 'django-admin startproject' using Django 2.0.4.

For more information on this file, see
https://docs.djangoproject.com/en/2.0/topics/settings/

For the full list of settings and their values, see
https://docs.djangoproject.com/en/2.0/ref/settings/
"""

import os
import pymysql

# connect mysql
pymysql.install_as_MySQLdb()
```
and you add DATABASE,
```Python:settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'todoList',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'db',
        'PORT': '3306',
        'TEST': {
            'NAME': 'test_todoList',
        },

    }
}
```

### Migrations
```console
$ docker-compose run python ./manage.py makemigrations
$ docker-compose run python ./manage.py migrate
```

### Create superuser
```console
$ docker-compose run python ./manage.py createsuperuser
```

### Start server in your local.
```console
$ docker-compose up -d
```

You access http://localhost .
If you will see this page, you success !

![django-image](https://user-images.githubusercontent.com/11535206/59239910-b6661280-8bf2-11e9-84e8-1733e94aa033.png)

## Licence
This starter kit is licensed under the MIT License - see the LICENSE.md file for details

## Donate
I receive BTC donate. Thank you.  
![QRL](https://user-images.githubusercontent.com/11535206/59242610-b0c0fa80-8bfb-11e9-9bdc-caa4764dc14e.png)  
3PfsHj5kYY6m9dGCcoQXb3ionu6cKJeG95

