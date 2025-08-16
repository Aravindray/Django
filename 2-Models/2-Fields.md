# Fields

<table>
    <thead>
        <tr>
            <th>Model Fields</th>
            <th>Constraints</th>
            <th>SQL Fields</th>
            <th>Description</th>
        </tr>
    <thead>
    <tbody>
        <tr>
            <td rowspan=2>CharField</td>
            <td>max_length=250</td>
            <td>VARCHAR(250)</td>
            <td>Column max length will be 250 characters only</td>
        </tr>
        <tr>
            <td>choice</td>
            <td>VARCHAR(250)</td>
            <td>This will use TextChoice field to create the dropdown</td>
        </tr>
        <tr>
            <td>SlugField</td>
            <td>max_length=250</td>
            <td>VARCHAR(250)</td>
            <td>Column max length will be 250 characters only. A slug contains only letters, numbers, underscores, or hyphens.</td>
        </tr>
        <tr>
            <td>TextField</td>
            <td>-</td>
            <td>TEXT</td>
            <td>-</td>
        </tr>
        <tr>
            <td rowspan=3>DateTimeField</td>
            <td>default</td>
            <td rowspan=3>DATETIME</td>
            <td>Define the default value, this statement <code>models.DateTimeField(default=timezone.now)</code> will create current time</td>
        </tr>
        <tr>
            <td>auto_now_add</td>
            <td>Store the new created object time automatically</td>
        </tr>
        <tr>
            <td>auto_now</td>
            <td>Store the modified object time automatically</td>
        </tr>
        <tr>
            <td rowspan=3>ForeignKey</td>
            <td>Relation Model Name</td>
            <td>FOREIGN KEY</td>
            <td>Create a relationship between two fields</td>
        </tr>
        <tr>
            <td>on_delete=models.CASCADE</td>
            <td>ON DELETE CASCADE</td>
            <td>Delete the existing field row when we delete the linked field</td>
        </tr>
        <tr>
            <td>related_name</td>
            <td>-</td>
            <td>Specify the name of the reverse relationship, for below <a href="#how-to-add-many-to-one-relationship">example</a> from User to Post</td>
        </tr>
    <tbody>
</table>


## How to add Many-to-One relationship?

With the help of `ForeignKey` we can define the relationship between two models.

```py
from django.conf import settings
from django.db import models

class Post(models.Model):
    author = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.CASCADE,
        related_name='blog_posts'
    )
```

Another Example:

```py
from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=100)

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

## How to add enumeration/dropdown fields in Database table with Django?

In the model class define a enumeration class with `TextChoices` and respected attributes / dropdown fields.

```py
class Post(models.Model):
    class Status(models.TextChoices):
        DRAFT = 'DF', 'Draft'
        PUBLISHED = 'PB','Published'

    ...
    status = models.CharField(
        max_length=2,
        choices=Status,
        default=Status.DRAFT
    )
```

_Let's look how to interect with Choice field_

```py
Post.Status.choices # Output: [('DF', 'Draft'), ('PB', 'Published')]
Post.Status.labels # Output: ['Draft', 'Published']
Post.Status.values # Output: ['DF', 'PB']
Post.Status.names # Output: ['DRAFT', 'PUBLISHED']
```
