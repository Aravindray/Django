# Admin Site

## What is admin site?

> Django comes with a built-in administration interface that is very useful for editing content. The
Django site is built dynamically by reading the model metadata and providing a production ready interface for editing content. You can use it out of the box, configuring how you want your models to be displayed in it. The `django.contrib.admin` application is already included in the INSTALLED\_APPS setting, so you don’t need to add it. - _Django 5 By Example_

## How to configure admin site?

1. First we need super user account, to create a super user account run this command in terminal `(my_env) >>> py manage.py createsuperuser` enter your desire username, email and password

2. After setup the super user, open the dev server by running this cmd `(my_env) >>> py manage.py runserver` and navigate to admin URL https://127.0.0.1:8000/admin/ then, enter username and password credentials that you created previously.

## How to add / register app model in admin site?

Every app file structure contain the admin.py module, we just need to import and register the model.

```py
from django.contrib import admin
from .models import Post

admin.site.register(Post)

# ---
# or
# ---

from django.contrib import admin
from .models import Post

@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
    ...
```

That's it you con view your model successfully in your admin site.

## How to customize the admin view?

We have to create the ModelAdmin sub-class, and add predefined attributes to customize the admin site.

```py
@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
    list_display = ['title', 'slug', 'author', 'publish', 'status']
    list_filter = ['status', 'created', 'publish', 'author']
    search_fields = ['title', 'body']
    prepopulated_fields = {'slug': ('title',)}
    raw_id_fields = ['author']
    date_hierarchy = 'publish'
    ordering = ['status', 'publish']
    show_facets = admin.ShowFacets.ALWAYS
```

## Attributes of ModelAdmin class!

- **list_display** : Enter the fields that you want to display it in admin site
- **list_filter** : Enter the fields that you want to filter it in admin site
- **search_fields** : Enter the fields that you want to search it in admin site
- **prepopulated_fields** : It takes object of field and it's parent field (Doesn't make any sense)
- **raw_id_fields** : Simplify the process of adding other model object with separate search
- **date_hierarchy** : to filter the display based on this field date
- **ordering** : order the display objects
- **show_facets** : This shows the count number in right side bar