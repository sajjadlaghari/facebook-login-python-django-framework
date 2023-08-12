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
]
```



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
Applying sessions.0001_initial… OK
```

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
Applying sessions.0001_initial… OK
```

#### Add new authentication methods in setting.py.

``` 
AUTHENTICATION_BACKENDS = [
  'social_core.backends.facebook.FacebookOAuth2',
  'social_core.backends.instagram.InstagramOAuth2',
  'django.contrib.auth.backends.ModelBackend',
]
````
#### Create a new folder with “templates” name into your root app 

``` create base.html ```

#### Add Below Code in base.html file

```
<!-- templates/base.html -->

{% load static %}
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css"
        integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous" />
    <link rel="stylesheet" href="{% static 'css/styles.css' %}" />
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
    <script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"></script>


    <title>Social Auth with Django</title>
</head>

<body>
    <div class="container-fluid">
        <div>
            <h1 class="text-white text-center">{% block title %}{% endblock %}</h1>
            <div class="card p-5">
                {% block content %}

                {% endblock %}
            </div>
        </div>
    </div>
</body>

</html>

````

#### Create home File in templates

``` home.html ```

### Add Below Code 

```
<!-- templates/home.html -->

{% extends 'base.html' %}
{% block title %} Home {% endblock %}
{% block content %}

<div class="container">
    <div class="row d-flex justify-content-center">
        <div class="col col-md-9 col-lg-7 col-xl-5">
            <div class="card" style="border-radius: 15px;">
                <div class="card-body p-4">
                    <div class="d-flex text-black">
                        <div class="flex-shrink-0">
                            {% for ass in backends.associated %}
                            {% if ass.provider == 'facebook' %}
                            <img src="{{ass.extra_data.picture.data.url}}" alt="Generic placeholder image"
                                class="img-fluid mx-3" style="width: 180px; border-radius: 10px; ">




                            {% endif %}
                            {% endfor %}

                        </div>
                        <div class="flex-grow-1 ms-3">
                            <h5 class="mb-1">{{ user.first_name }} {{ user.last_name }}</h5>
                            <p class="mb-2 pb-1" style="color: #2b2a2a;">{{ user.username }}</p>
                            <div class="d-flex justify-content-start rounded-3 p-2 mb-2"
                                style="background-color: #efefef;">

                            </div>
                            <div class="d-flex pt-1">

                                <button type="button" class="btn btn-danger flex-grow-1 w-100 mx-2">
                                    <a href="{% url 'logout' %}" class="text-white text-decoration-none">

                                        Logout
                                    </a>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>


{% endblock %}

```
