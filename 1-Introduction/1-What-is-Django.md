# What is Django?

Django is free and open-source, back-end web development framework based on Python programming language.

## How to setup & create Django project?

### 1. How to Install Python!

1. Since Django is Python framework, we first need to install Python from [Python.org](https://www.Python.org/downloads/)
2. In the installation wizard make sure to enable (select) the **Add Python 3.x to PATH** and select **Install Now**, Python will install automatically.
3. To confirm whether Python installed successfully or not, open the windows terminal and type `py --version`

### 2.a. How to Create Virtual Environment!

1. It is recommend to use dedicated virtual environment for each Django project, So how to create Virtual Environment?
2. To create a virtual environment, first create a directory (aka folder) `D:\projects\folder_name`, then open the command prompt navigate to that folder. (check out [Basic Command Line Operations](obsidian://open?vault=Notes&file=How-to-do-it#how-to create-or-delete-folder-and-files-using-windows-command-prompt))
3. In that folder create a virtual environment with this command `$> py -m venv env_name`
4. Above command will create the virtual environment directory called *env_name* and we must need to activate it before installing Django.
5. To activate the environment use this command `$> env_name\Scripts\activate`
6. You know that virtual environment is started when you see that the prompt in your terminal is prefixed with *env_name* like this `(env_name) $> `
7. How to deactivate virtual environment?, just type `deactivate` in the terminal.

### 2.b. How to create a Virtual Environment in a separate folder?

1. To create a virtual environment, first create a directory (aka folder) `D:\projects\to-do`, then open the folder in the command prompt.
2. Inside that folder (to-do) create another folder and name it `env`
3. then move into the `env` folder and create a virtual environment with this cmd `$> py -m venv env_name`

_then follow steps from above 2.a. - 4 to 7_

### 3. How to Install Django?

1. Before installing Django, we need to make sure that we have the latest version of pip, so to update pip use this command `(env_name) $> python -m pip install --upgrade pip`
2. That's all, Now we are ready to install Django, type this command in your terminal `(env_name) $> pip install django`
3. Django now installed, you are good to go!

### 4. How to Create Django Project?

**Note: Don't forget to add period (or dot) . at the end & avoid naming project after built-in Python or Django modules**
1. To create a project use this command `(env_name) $> django-admin startproject project_name .`
2. That's it, a basic file structure for your project is ready.

for example, if I create a project **mysite** (without .), below structure will be created:

```bash ln:false
.
└── mysite/
    ├── manager.py
    └── mysite/
        ├── __init__.py
        ├── asgi.py
        ├── settings.py
        ├── urls.py
        └── wsgi.py
```

### 5. How to Create Django application (app)?

1. To create a app use this command `(env_name) $> py manage.py startapp app_name`
2. An app consist of models, views, templates and URLS structure will be created.

for example, If I create an app with the name **blog**, below structure will be created:

```bash ln:false
.
└── blog/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── migrations/
    │   ├── __init__.py
    ├── models.py
    ├── tests.py
    └── views.py
```

> [!tip] Hint
> To create above file structure visit [Tree Nathanfriend](https://tree.nathanfriend.com/)

### 6. How to activate the application?

Open `settings.py` file and navigate to INSTALLED_APPS settings, then add the app config like below:

```py
INSTALLED_APPS = [
    ...
    'blog.apps.BlogConfig',
]
```

### 7. How to Change the Timezone?

_Before Migrate, Change the project timezone_

Open the settings.py file of the project directory, and edit the  **TIME_ZONE** variable, for IST `TIME_ZONE = "Asia/Kolkata"`

### 8. Now it is Good time to change backend database!

If you decided to user PostgreSQL first install psycopg2 library with this cmd `pip install psycopg2`

And change the database settings like below

```py title:"change project database"
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "database_name",
        "HOST": "localhost",
        "USER": "user_name",
        "PASSWORD": "password",
        "PORT": "5432",
    }
}
```

### 9. How to Migrate for creating database table?

_If you defined the model for the app, first make a migrations and mirgrate it, else simply migrate it!_

Open the terminal and type this cmd `(evn_name) $> py manage.py makemigrations app_name` and then type `(env_name) $> py manage.py migrate`

### 10. How to run the development server?

`(env_name) $> py manage.py runserver` command will start the lightweight web server to run our code quickly.

### 11. How to create a super user or Admin?

1. In the terminal enter this command `(env_name) $> py manage.py createsuperuser`
2. Then enter the Username, email address and password.
3. for more check out this [admin](../Admin/Admin.ipynb) article

**Do You Know?**
In `$> py -m venv env_name` where
`$>` indicate terminal prompt
`py` is short form of Python
`-m` is used to run module as a script mode
`venv` is a *package* name
`env_name` is actual virtual environment name

**Basic Notations**

This is a Terminal prompt `$>`
This is a Python prompt `>>>`

**What is the difference between a *package* and a *library*?**

A package is the collection of modules, while a library is a collection of packages. Module is a file with `.py` extension, a package is a folder which contain reusable modules. we can import module and package with `import` statement.

**What is pip?**

Pip (Pip Installs Packages) is a package manager for python, that allows to install and manage python packages.

Go to [Next >>](./2-Django-Overview.md)