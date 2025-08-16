# Introduction - What is Model?

Model is a class which represent database as an objects.

Each model class represent single database table and each attribute represent database tables column/field.

```py
# Source from Django 5 by Example book
from django.db import models


class Post(models.Model):
    title = models.CharField(max_length=250)
    slug = models.SlugField(max_length=250)
    body = models.TextField()

    def __str__(self):
        return self.title
```

We have to import the models module from `django.db` and create a sub-class with models.Model. Once we define the model we must make sure that our model is in sync with database by using this command `(env) >>> py manage.py makemigrations app_name` (app_name: blog)

To create our defined model class into database as a table we need to add our app to the INSTALLED_APP list **blog.apps.BlogConfig** in `settings.py` file and run this command `(env) >>> py manage.py migrate`

from the above command, a table with the name **blog_post** will be created in the database, where blog - app name & post - model name.

## What is Meta Class?

This class defines metadata for model, we can define attributes in this class for specific performance.

### Attributes of Meta Class

- Ordering

  > [!question] How to define a default sort order?
  >> [!todo] Just add `ordering` attribute in the Meta Class
  > ```py
  > class Meta:
  > 	ordering = ['-publish']
  > ```

- indexes

  > [!question] How to add a database index?
  >> [!todo] Just add `indexes` attribute in the Meta Class
  > ```py
  >  class Meta:
  > 	 indexes = [ models.Index(fields=['-publish']) ]
  > ```