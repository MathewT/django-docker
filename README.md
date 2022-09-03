# django-docker

## Commands

### create new project site

```bash
docker-compose run web django-admin startproject my_site_project  .
```

### exec (bash) into running web container

```bash
docker-compose  exec web /bin/bash
```

### launch psql from inside running web container

```bash
psql "host=db port=5432 dbname=postgres user=postgres"
```

## Notes

For Postgresql connectivity, fix `settings.py` like this:

```python
import os

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('POSTGRES_NAME'),
        'USER': os.environ.get('POSTGRES_USER'),
        'PASSWORD': os.environ.get('POSTGRES_PASSWORD'),
        'HOST': 'db',
        'PORT': '5432',
    }
}
```

Fix `ALLOWED_HOSTS` in `settings.py`

```python
ALLOWED_HOSTS = ['0.0.0.0', '127.0.0.1', 'localhost', '[::1]']
```

## Links

https://docs.docker.com/samples/django/

https://docs.djangoproject.com/en/4.1/intro/tutorial01/

https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Tutorial_local_library_website

https://django-bootstrap-v5.readthedocs.io/en/latest/quickstart.html