## Table of Content

- [What is Django?](#what-is-django)
  - [Introduction](#introduction)
  - [How to setup \& create Django project?](#how-to-setup--create-django-project)
    - [1. How to Install Python!](#1-how-to-install-python)
    - [2. How to Create Virtual Environment!](#2-how-to-create-virtual-environment)
    - [3. How to Install Django?](#3-how-to-install-django)
    - [4. How to Create Django Project?](#4-how-to-create-django-project)
    - [5. How to Create Django application (app)?](#5-how-to-create-django-application-app)

# What is Django?

## Introduction

Django is free and open-source, back-end web development framework based on Python programming language.

## How to setup & create Django project?

### 1. How to Install Python!

1. Since Django is Python framework, we first need to install Python from [Python.org](https://www.Python.org/downloads/)
2. In the installation wizard make sure to enable (select) the **Add Python 3.x to PATH** and select **Install Now**, Python will install automatically.
3. To confirm whether Python installed successfully or not, open the windows terminal and type ```py --version```

### 2. How to Create Virtual Environment!

1. It is recommend to use dedicated virtual environment for each Django project, So how to create Virtual Environment? (check below)
2. To create a virtual environment, first create a directory (aka folder) ```D:\projects\folder_name```, then open the command prompt navigate to that folder. (check out [Basic Command Line Operations](https://github.com/Aravindray/Notes/blob/main/How-to-do-it.md))
3. In that folder create a virtual environment with this command ```$> py -m venv env_name```
4. Above command will create the virtual environment directory called *env_name* and we must need to activate before installing django.
5. To activate the environment use this command ```$> env_name\Scripts\activate```
6. You know that virtual environment is started when you see that the prompt in your terminal is prefixed with *env_name* like this ```(env_name) $> ```
7. How to deactivate virtual environment?, just type ```deactivate``` in the terminal.

### 3. How to Install Django?

1. Before installing django, we need to make sure that we have the latest version of pip, so to update pip use this command ```(env_name) $> python -m pip install --upgrade pip```
2. That's all, Now we are ready to install Django, type this command in your terminal ```(env_name) $> pip install django```
3. Django now installed, you are good to go!

### 4. How to Create Django Project?

1. To create a project use this command ```(env_name) $> django-admin startproject project_name .``` <br> **Note: Don't forget to add period (or dot) . at the end & avoid naming project after built-in Python or Django modules**
2. That's it, a basic file structure for your project is ready.

<hr>

**Do You Know?** <br>
In ```$> py -m venv env_name``` where <br>
```$>``` indicate terminal prompt <br>
```py``` is short form of Python <br>
```-m``` is used to run module as a script mode <br>
```venv``` is a *package* name <br>
```env_name``` is actual virtual environment name

**What is the difference between a *package* and a *library*?**

A package is the collection of modules, while a library is a collection of packages. <br> Module is a file with ```.py``` extension, a package is a folder which contain reusable modules. we can import module and package with ```import``` statement.

**What is pip?**

Pip (Pip Installs Packages) is a package manager for python, that allows to install and manage python packages.

### 5. How to Create Django application (app)?

1. To create a app use this command ```(env_name) $> py manage.py startapp app_name```
2. A app consist of module, views, templates and URLS.