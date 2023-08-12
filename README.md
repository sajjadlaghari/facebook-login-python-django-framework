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
'facbook',  #add here your installed APP 
]

```


#### Install the social-auth-app-django modul
``` pip install social-auth-app-django ```


#### Add New Installed APP in setting.py INSTALLED_APPS

``` INSTALLED_APPS = [
'django.contrib.admin',
'django.contrib.auth',
'django.contrib.contenttypes',
'django.contrib.sessions',
'django.contrib.messages',
'django.contrib.staticfiles',
'facbook',  #add here your installed APP
'social_django', # Social Django Module
] ```



#### let’s migrate the database.
``` py manage.py migrate  ```

#### When you migrate you can see all the performed operations on database.

``` py manage.py migrate
Operations to perform:
Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
Applying contenttypes.0001_initial… OK
Applying auth.0001_initial… OK
Applying admin.0001_initial… OK
Applying admin.0002_logentry_remove_auto_add… OK
Applying admin.0003_logentry_add_action_flag_choices… OK
Applying contenttypes.0002_remove_content_type_name… OK
Applying auth.0002_alter_permission_name_max_length… OK
Applying auth.0003_alter_user_email_max_length… OK
Applying auth.0004_alter_user_username_opts… OK
Applying auth.0005_alter_user_last_login_null… OK
Applying auth.0006_require_contenttypes_0002… OK
Applying auth.0007_alter_validators_add_error_messages… OK
Applying auth.0008_alter_user_username_max_length… OK
Applying auth.0009_alter_user_last_name_max_length… OK
Applying auth.0010_alter_group_name_max_length… OK
Applying auth.0011_update_proxy_permissions… OK
Applying sessions.0001_initial… OK ```

