# Model Manager

## What is Model Manager

Each Django model has at least one manager, and the default manager is called objects. You get a QuerySet object using your model manager.

## How to create a custom model manager?

There are two ways to add or customize managers for your models: you can add extra manager methods to an existing manager or create a new manager by modifying the initial QuerySet that the manager returns. The first method provides you with a QuerySet notation like Post.objects.my_manager(), and the latter provides you with a QuerySet notation like Post.my_manager.all().

```py title:"models.py"
class PublishedManager(models.Manager):
    def get_queryset(self):
        return (super().get_queryset().filter(status=Post.Status.PUBLISHED))

Class Post(models.Model):
    # ...

    objects = models.Manager()
    published = PublishedManager()

    # ...
```

The first manager declared in a model becomes the default manager. You can use the Meta attribute default_manager_name to specify a different default manager. If no manager is defined in the model, Django automatically creates the objects default manager for it. If you declare any managers for your model but you want to keep the objects manager as well, you have to add it explicitly to your model. In the preceding code, we have added the default objects manager and the published custom manager to the Post model.