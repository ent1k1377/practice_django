# Django Docs 4.x

Полная документация [django](https://docs.djangoproject.com/en/4.1/).

## Static Files

<https://docs.djangoproject.com/en/4.1/ref/contrib/staticfiles/>

Настройки осуществляются с помощью встроенного приложения `django.contrib.staticfiles`.<br>
`django.contrib.staticfiles` собирает статические файлы в одно место.

___

### STATIC_ROOT

Устанавливает абсолютный путь к папке в которой будут собираться все статические файлы проекта. То есть в этой папке
будут храниться вся статика из всех приложений.<br>
Бесполезен при локальной разработке, нужен только при развертывании в Nginx, Apache и т.д.

```
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

### STATIC_URL

URL для использования при обращении к статическим файлам, расположенным в STATIC_ROOT.

```
STATIC_URL = 'static/'
```

### STATICFILES_DIRS

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