## Migrations

> Migrations are Django’s way of propagating changes that you make to your models (such as adding a field, deleting a model, etc.) into your database schema. They’re designed in such a way that they are mostly automatic, but you’ll need to know when to make the migrations, when to run them, and the common problems you might face.
    - Django Migration [Docs](https://docs.djangoproject.com/en/1.10/topics/migrations/#module-django.db.migrations)


### Creating a migration

* We recommend you to create migrations per app, where the changes are only about a single issue or feature.

```
# migration only for jobs app
python manage.py makemigrations jobs
```

* Always create named migrations. You can name migrations by passing `-n` or `--name` argument.

```
python manage.py makemigrations jobs -n=execution_time_limit
# or
python manage.py makemigrations jobs --name=execution_time_limit
```

* While creating migrations on the local environment, don't forget to add the development settings.

```
python manage.py makemigrations --settings=settings.dev
```

The following is an example of a complete named migration for the `jobs` app, where in an execution time limit field is added to the `Submission` model:

```
python manage.py makemigrations jobs --name=execution_time_limit --settings=settings.dev
```

* Files whuch are created after running `makemigrations` should be committed along with other files.

* While creating a migration for your concerned change, it might happen that some other changes are also there in the migration file. Like adding a `execution_time_limit` field on `Submission` model also brings in the change for `when_made_public` being added. In that case, open an new issue(https://github.com/Cloud-CV/EvalAI/issues/new) and clearly mention the issue  there. If possible then fix the issue yourself, by opening a new branch and creating migrations only for the concerned part. The idea here is that a commit should only include its concerned migration changes and nothing else.
