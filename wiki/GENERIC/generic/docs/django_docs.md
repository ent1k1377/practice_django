# Django Docs 4.1

Полная документация [django](https://docs.djangoproject.com/en/4.1/).

## Static Files

<https://docs.djangoproject.com/en/4.1/ref/contrib/staticfiles/>

Настройки осуществляются с помощью встроенного приложения `django.contrib.staticfiles`.<br>
`django.contrib.staticfiles` собирает статические файлы в одно место.

___

### STATIC_ROOT

Дефолт: `None`

Устанавливает абсолютный путь к папке в которой будут собираться все статические файлы проекта. То есть в этой папке
будут храниться вся статика из всех приложений.<br>
Бесполезен при локальной разработке, нужен только при развертывании в Nginx, Apache и т.д.

```
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

### STATIC_URL

Дефолт: `None`

URL для использования при обращении к статическим файлам, расположенным в STATIC_ROOT.

```
STATIC_URL = 'static/'
```

### STATICFILES_DIRS

Дефолт: `[]`

Список папок/приложений в которых будут изъяты дополнительные статические файлы.

```
STATICFILES_DIRS = (
    BASE_DIR / 'static',
)
```

### STATICFILES_STORAGE

Дефолт: `'django.contrib.staticfiles.storage.StaticFilesStorage'`<br>
Забей на это.

### STATICFILES_FINDERS

Дефолт:

    [
        'django.contrib.staticfiles.finders.FileSystemFinder',
        'django.contrib.staticfiles.finders.AppDirectoriesFinder',
    ]

Список поисковых серверов, которые умеют находить статические файлы в разных местах.
___

## MEDIA

<https://docs.djangoproject.com/en/4.1/topics/files/><br>
<https://docs.djangoproject.com/en/4.1/howto/static-files/>

### MEDIA_ROOT

Дефолт: `''`

Устанавливает абсолютный путь к папке в которой будут собираться все медиа файлы.

Пример:
`MEDIA_ROOT = os.path.join(BASE_DIR, 'media')`

### MEDIA_URL

Дефолт: `''`

URL-адрес, который обрабатывает медиафайлы из MEDIA_ROOT и используется для управления сохраненными файлами.

Пример:
`MEDIA_URL = '/media/'`

### Дополнительно

Во время отладки/разработки нужно включить MEDIA_URL таким способом, чтобы можно было загружать файлы с сайта в хранилище/диск.

```
# файл app/app/urls.py
if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```