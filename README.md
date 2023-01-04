# Django project boilerplate for Vs Code

Based on [Настройка Visual Studio Code для Django](https://habr.com/ru/post/701800/)

## Install

```shell
pip install django black isort pylint pylint-django mypy django-stubs
# or
pipenv install --dev django black isort pylint pylint-django mypy django-stubs
# or
poetry add --dev django black isort pylint pylint-django mypy django-stubs
```

## Configuration files

### .vscode/settings.json

```json
{
  "editor.formatOnSave": true,
  "python.formatting.provider": "black",
  "python.formatting.blackArgs": ["--line-length=120"],
  "python.linting.pylintEnabled": true,
  "python.linting.enabled": true,
  "python.linting.lintOnSave": true,
  "python.linting.pylintArgs": [
    "--load-plugins",
    "pylint_django",
    "--django-settings-module=core.settings",
    "--max-line-length=120"
  ],

  "editor.codeActionsOnSave": {
    "source.organizeImports": true
  },
  "python.linting.mypyEnabled": true
}
```

## .mypy.ini

```ini
[mypy]
plugins =
    mypy_django_plugin.main

[mypy.plugins.django-stubs]
django_settings_module = "core.settings"
```

## .isort.cfg

```ini
[settings]
profile=black
```
