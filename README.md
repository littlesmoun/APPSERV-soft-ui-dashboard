# Django Soft UI Dashboard

Admin dashboard generated by AppSeed in **Django** Framework. Designed for those who like bold elements and beautiful websites, **Soft UI Dashboard** is ready to help you create stunning websites and webapps. Soft UI Dashboard is built with over 70 frontend individual elements, like buttons, inputs, navbars, navtabs, cards or alerts, giving you the freedom of choosing and combining.

<br />

- UI Kit: **[Soft UI Dashboard](https://bit.ly/2Q1uIfK)** (Free Version) provided by **Creative-Tim**
- SQLite Database, Django Native ORM
- Modular design, clean codebase
- Session-Based Authentication, Forms validation
- Deployment scripts: Docker, Gunicorn / Nginx
- Support via **Github** (issues tracker) and [Discord](https://discord.gg/fZC6hup).

<br />

> Links

- [Django Soft Dashboard](https://django-soft-ui-dashboard.appseed-srv1.com/) - LIVE Demo
- [Django Soft Dashboard](https://docs.appseed.us/products/django-dashboards/soft-ui-dashboard) - Product documentation

<br />

## Want more? Go PRO!

PRO versions include **Premium UI Kits**, Lifetime updates and **24/7 LIVE Support** (via [Discord](https://discord.gg/fZC6hup))

| [Django Datta PRO](https://appseed.us/admin-dashboards/django-dashboard-dattaable-pro) | [Django Material PRO](https://appseed.us/admin-dashboards/django-dashboard-material-pro) | [Django Volt PRO](https://appseed.us/admin-dashboards/django-dashboard-volt-pro) |
| --- | --- | --- |
| [![Django Datta PRO](https://raw.githubusercontent.com/app-generator/django-dashboard-dattaable-pro/master/media/django-dashboard-dattaable-pro-screen.png)](https://appseed.us/admin-dashboards/django-dashboard-dattaable-pro) | [![Django Material PRO](https://raw.githubusercontent.com/app-generator/django-dashboard-material-pro/master/media/django-dashboard-material-pro-screen.png)](https://appseed.us/admin-dashboards/django-dashboard-material-pro) | [![Django Volt PRO](https://raw.githubusercontent.com/app-generator/django-dashboard-volt-pro/master/media/django-dashboard-volt-pro-screen.png)](https://appseed.us/admin-dashboards/django-dashboard-volt-pro)

<br />

![Django Soft UI Dashboard - Seed project generated by AppSeed.](https://user-images.githubusercontent.com/51070104/119937082-d5524080-bf92-11eb-83b2-19034824e934.png)

<br />

## How to use it

```bash
$ # Get the code
$ git clone https://github.com/app-generator/django-soft-ui-dashboard.git
$ cd django-soft-ui-dashboard
$
$ # Virtualenv modules installation (Unix based systems)
$ virtualenv env
$ source env/bin/activate
$
$ # Virtualenv modules installation (Windows based systems)
$ # virtualenv env
$ # .\env\Scripts\activate
$
$ # Install modules - SQLite Storage
$ pip3 install -r requirements.txt
$
$ # Create tables
$ python manage.py makemigrations
$ python manage.py migrate
$
$ # Start the application (development mode)
$ python manage.py runserver # default port 8000
$
$ # Start the app - custom port
$ # python manage.py runserver 0.0.0.0:<your_port>
$
$ # Access the web app in browser: http://127.0.0.1:8000/
```

> Note: To use the app, please access the registration page and create a new user. After authentication, the app will unlock the private pages.

<br />

## Code-base structure

The project is coded using a simple and intuitive structure presented bellow:

```bash
< PROJECT ROOT >
   |
   |-- core/                               # Implements app logic and serve the static assets
   |    |-- settings.py                    # Django app bootstrapper
   |    |-- wsgi.py                        # Start the app in production
   |    |-- urls.py                        # Define URLs served by all apps/nodes
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component
   |         |    |-- sidebar.html         # Sidebar component
   |         |    |-- footer.html          # App Footer
   |         |    |-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                  # Master pages
   |         |    |-- base-fullscreen.html # Used by Authentication pages
   |         |    |-- base.html            # Used by common pages
   |         |
   |         |-- accounts/                 # Authentication pages
   |         |    |-- login.html           # Login page
   |         |    |-- register.html        # Register page
   |         |
   |      index.html                       # The default page
   |     page-404.html                     # Error 404 page
   |     page-500.html                     # Error 404 page
   |       *.html                          # All other HTML pages
   |
   |-- authentication/                     # Handles auth routes (login and register)
   |    |
   |    |-- urls.py                        # Define authentication routes  
   |    |-- views.py                       # Handles login and registration  
   |    |-- forms.py                       # Define auth forms  
   |
   |-- app/                                # A simple app that serve HTML files
   |    |
   |    |-- views.py                       # Serve HTML pages for authenticated users
   |    |-- urls.py                        # Define some super simple routes  
   |
   |-- requirements.txt                    # Development modules - SQLite storage
   |
   |-- .env                                # Inject Configuration via Environment
   |-- manage.py                           # Start the app - Django default start script
   |
   |-- ************************************************************************
```

<br />

> The bootstrap flow

- Django bootstrapper `manage.py` uses `core/settings.py` as the main configuration file
- `core/settings.py` loads the app magic from `.env` file
- Redirect the guest users to Login page
- Unlock the pages served by *app* node for authenticated users

<br />

## Deployment

The app is provided with a basic configuration to be executed in [Docker](https://www.docker.com/), [Gunicorn](https://gunicorn.org/), and [Waitress](https://docs.pylonsproject.org/projects/waitress/en/stable/).

### [Docker](https://www.docker.com/) execution
---

The application can be easily executed in a docker container. The steps:

> Get the code

```bash
$ git clone https://github.com/app-generator/django-soft-ui-dashboard.git
$ cd django-soft-ui-dashboard
```

> Start the app in Docker

```bash
$ sudo docker-compose pull && sudo docker-compose build && sudo docker-compose up -d
```

Visit `http://localhost:5005` in your browser. The app should be up & running.

> Create Django `superuser` 

```bash
$ # Get Container ID
$ docker ps
$ 
$ # Call docker exec and CREATE the Superuser
$ docker exec -it <APPSEED_CONTAINER_ID> python manage.py createsuperuser
```
 
<br />

### [Gunicorn](https://gunicorn.org/)
---

Gunicorn 'Green Unicorn' is a Python WSGI HTTP Server for UNIX.

> Install using pip

```bash
$ pip install gunicorn
```
> Start the app using gunicorn binary

```bash
$ gunicorn --bind=0.0.0.0:8001 core.wsgi:application
Serving on http://localhost:8001
```

Visit `http://localhost:8001` in your browser. The app should be up & running.


<br />

### [Waitress](https://docs.pylonsproject.org/projects/waitress/en/stable/)
---

Waitress (Gunicorn equivalent for Windows) is meant to be a production-quality pure-Python WSGI server with very acceptable performance. It has no dependencies except ones that live in the Python standard library.

> Install using pip

```bash
$ pip install waitress
```
> Start the app using [waitress-serve](https://docs.pylonsproject.org/projects/waitress/en/stable/runner.html)

```bash
$ waitress-serve --port=8001 core.wsgi:application
Serving on http://localhost:8001
```

Visit `http://localhost:8001` in your browser. The app should be up & running.

<br />

## Credits & Links

- [Django](https://www.djangoproject.com/) - The official website
- [Boilerplate Code](https://appseed.us/boilerplate-code) - Index provided by **AppSeed**
- [Boilerplate Code](https://github.com/app-generator/boilerplate-code) - Index published on Github

<br />

---
Django Soft UI Dashboard - Provided by **AppSeed** [App Generator](https://appseed.us/app-generator).
