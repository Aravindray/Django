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

**Model form**

To create a model form in Django and add a new item to your Category model, follow these steps:

1. Define Your Model

	Ensure your Category model is defined in models.py with a name field.
	
```py
from django.db import models
class Category(models.Model):
	name = models.CharField(max_length=100)
	
	def __str__(self):
		return self.name
```

2. Create a ModelForm

	Create a CategoryForm in forms.py to handle the form logic.

```py
from django import forms
from .models import Category

class CategoryForm(forms.ModelForm):
    class Meta:
        model = Category
        fields = ['name']
```

3. Create a View to Handle the Form

	In views.py, create a view to display the form and handle form submissions.

```py
from django.shortcuts import render, redirect
from .forms import CategoryForm

def add_category(request):
    if request.method == 'POST':
        form = CategoryForm(request.POST)
        if form.is_valid():
            form.save()  # Save the new category to the database
            return redirect('category_list')  # Redirect to a category list or another page
    else:
        form = CategoryForm()
    return render(request, 'add_category.html', {'form': form})
```

4. Create a Template

	Create a template add_category.html to render the form.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Add Category</title>
</head>
<body>
    <h1>Add New Category</h1>
    <form method="post">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Add Category</button>
    </form>
</body>
</html>
```

5. Configure URL

	Add a URL pattern in urls.py to map to the add_category view.

```py
from django.urls import path
from . import views

urlpatterns = [
    path('add-category/', views.add_category, name='add_category'),
]
```

6. Run the Server and Test

	Start your Django development server: python manage.py runserver.
	Navigate to /add-category/ in your browser.
	Fill out the form and submit to add a new category.

These setup will allow you to create a new category using a Django model form.