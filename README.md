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


#### Open setting.py

```

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
                'social_django.context_processors.backends', # Add this line
                'social_django.context_processors.login_redirect', # Add this line

            ],
        },
    },
]



````


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
#### Create a new folder with “templates” name into your root app and add Folder name 

``` 
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'], # Add Your templates folder name here
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
              ],
            },
    },
]

```

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

``` create login.html  ```

#### Add Below code in login.html file

``` 
<!-- templates/login.html -->

{% extends 'base.html' %}
{% block content %}
<div class="login-form">
    <form action="/examples/actions/confirmation.php" method="post">
        <h2 class="text-center">Sign in</h2>
        <div class="form-group">
            <div class="input-group">
                <div class="input-group-prepend">
                    <span class="input-group-text">
                        <span class="fa fa-user"></span>
                    </span>
                </div>
                <input type="text" class="form-control" name="username" placeholder="Username" required="required">
            </div>
        </div>
        <div class="form-group">
            <div class="input-group">
                <div class="input-group-prepend">
                    <span class="input-group-text">
                        <i class="fa fa-lock"></i>
                    </span>
                </div>
                <input type="password" class="form-control" name="password" placeholder="Password" required="required">
            </div>
        </div>
        <div class="form-group">
            <button type="submit" class="btn btn-primary login-btn btn-block">Sign in</button>
        </div>
        <div class="clearfix">
            <label class="float-left form-check-label"><input type="checkbox"> Remember me</label>
            <a href="#" class="float-right">Forgot Password?</a>
        </div>
        <div class="or-seperator"><i>or</i></div>
        <p class="text-center">Login with your social media account</p>
        <div class="text-center social-btn">
            <a href="{% url 'social:begin' 'facebook' %}" class="btn btn-secondary w-100"><i
                    class="fa fa-facebook"></i>&nbsp; Sign in with Facebook</a>
        </div>
    </form>
    <p class="text-center text-muted small">Don't have an account? <a href="#">Sign up here!</a></p>
    {% endblock %}
```

#### Create static folder in Your Project Root and inside static filder create css folder

#### Add static folder in setting.py

```
STATIC_URL = '/static/'
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static')
]
```

``` 
create file styles.css
```
#### Add Below code in styles.css file
```
.login-form {
  width: 400px;
  margin: 30px auto;
}
.login-form form {
  margin-bottom: 15px;
  background: #f7f7f7;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
  padding: 30px;
}
.login-form h2 {
  margin: 0 0 15px;
}
.form-control,
.login-btn {
  border-radius: 2px;
}
.input-group-prepend .fa {
  font-size: 18px;
}
.login-btn {
  font-size: 15px;
  font-weight: bold;
  min-height: 40px;
}
.social-btn .btn {
  border: none;
  margin: 10px 3px 0;
  opacity: 1;
}
.social-btn .btn:hover {
  opacity: 0.9;
}
.social-btn .btn-secondary,
.social-btn .btn-secondary:active {
  background: #507cc0 !important;
}
.social-btn .btn-info,
.social-btn .btn-info:active {
  background: #64ccf1 !important;
}
.social-btn .btn-danger,
.social-btn .btn-danger:active {
  background: #df4930 !important;
}
.or-seperator {
  margin-top: 20px;
  text-align: center;
  border-top: 1px solid #ccc;
}
.or-seperator i {
  padding: 0 10px;
  background: #f7f7f7;
  position: relative;
  top: -11px;
  z-index: 1;
}
```


#### Open facebook/views.py and copy-paste below code into the file.

```
from django.shortcuts import render
from django.contrib.auth.decorators import login_required
 
def login(request):
    return render(request, 'login.html')
 
@login_required
def home(request):
    return render(request, 'home.html')
```

#### Open FacebookLogin/urls.py and copy-paste below code into the file.

```
from django.contrib import admin
from django.urls import path, include
from django.contrib.auth import views as auth_views
from facebook import views
 
urlpatterns = [
  path('admin/', admin.site.urls),         
  path("login/", views.login, name="login"),
  path("logout/", auth_views.LogoutView.as_view(), name="logout"),
  path('social-auth/', include('social_django.urls', namespace="social")),
  path("", views.home, name="home"),
]

```

#### Open FacebooLogin/settings.py file and set these URL variables.

``` 
LOGIN_URL = 'login'
LOGIN_REDIRECT_URL = 'home'
LOGOUT_URL = 'logout'
LOGOUT_REDIRECT_URL = 'login'

SOCIAL_AUTH_FACEBOOK_SCOPE = ['email', 'user_link']
SOCIAL_AUTH_FACEBOOK_PROFILE_EXTRA_PARAMS = {
  'fields': 'id, name, email, picture.type(large), link'
}
SOCIAL_AUTH_FACEBOOK_EXTRA_DATA = [
    ('name', 'name'),
    ('email', 'email'),
    ('picture', 'picture'),
    ('link', 'profile_url'),
]


```

#### Now you need to connect your Facebook app with your Django project.

#### Open FacebooLogin/settings.py file and set these URL variables.

``` 
SOCIAL_AUTH_FACEBOOK_KEY = YOUR_APP_KRY # App ID
SOCIAL_AUTH_FACEBOOK_SECRET = YOUR_APP_SECRET # App Secret
```

#### Open below url

``` 
 https://developers.facebook.com/apps
```

#### After login create My Apps

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/389c0a11-9f6a-4678-8c8d-f10d39107e37)

#### Create your app

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/c798316a-bad4-4cd1-98b3-af4c5b087a15)

#### Enter Your App Name

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/49d1e9f1-0470-49ce-85e0-4b1858dc54dc)


#### Go to setting > basics. And set the App Domains as localhost.

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/637360a9-f228-4418-9f87-44d2733dfe82)

#### Site url if localhost

![image](https://github.com/sajjadlaghari/facebook-login-python-django-framework/assets/68752819/64daff2b-6530-42e5-b955-2031d964dd0d)


#### Now start server.
``` python manage.py runserver ```

