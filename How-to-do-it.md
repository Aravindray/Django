## Table Of Content
- [Settings](#settings)
  - [How to change backend database?](#how-to-change-backend-database)

# Settings

## How to change backend database?

**To connect PostgreSQL with Django**, follow these steps:

1. Make sure that you have install Postgres and Create the PostgreSQL Database, Log in to PostgreSQL as admin / superuser account `$> psql -U postgres`

For More: Check out this [PostgreSQL](https://github.com/Aravindray/PostgreSQL/) Repository

**Create a user**: CREATE USER user_name WITH PASSWORD 'password';
**Create a database**: CREATE DATABASE database_name WITH OWNER 'user_name' ENCODING 'UTF8';
**Create a user and grant privileges**: GRANT ALL PRIVILEGES ON DATABASE database_name TO user_name;

2. Install psycopg2: Ensure PostgreSQL is installed on your system. Install the psycopg2 library, which acts as the PostgreSQL adapter for Python: `pip install psycopg2`

3. Update Django Settings: Open your Django project's _settings.py_ file and configure the DATABASES dictionary for PostgreSQL:
   - For security purpose store all the credentials in _.env_ file and install python-decouple library with this cmd `pip install python-decouple`
   - And import the _config_ module like this `from decouple import config`

```py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': config("DB_Name"),
        'USER': config("DB_Username"),
        'PASSWORD': config("DB_Password"),
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```


4. Apply Migrations: Run the following commands to apply migrations and set up your database schema: `python manage.py makemigrations` & `python manage.py migrate`

5. Test the Connection: Run the Django development server: `python manage.py runserver`