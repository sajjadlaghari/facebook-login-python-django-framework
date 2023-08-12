### facebook-login-python-django-framework

### Demo login page

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/ef48ebba-00e4-43a6-ad71-f16271a18724)


### Home Page

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/a00b177e-2da1-4bef-a400-d06ae30f010e)



#### Create Virtual Enviroment

``` python -m venv SocialLogin  ```


#### Active Enviroment

``` cd SocialLogin ```
``` cd Scripts cd Activate ```

#### Install Django in your enviroment

``` pip install django  ```


#### Create your project. You can give it any name.
``` django-admin startproject FacebookLogin ```

``` cd FacebookLogin ```

#### Create App
```  python manage.py startapp facbook ```

#### Add New Installed APP in setting.py INSTALLED_APPS

```
INSTALLED_APPS = [
'django.contrib.admin',
'django.contrib.auth',
'django.contrib.contenttypes',
'django.contrib.sessions',
'django.contrib.messages',
'django.contrib.staticfiles',
'facbook',  #add here in Installed APp 
]

```


#### Install the social-auth-app-django modul
``` pip install social-auth-app-django ```
