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

### .editorconfig

```ini
# https://editorconfig.org/

root = true

[*]
indent_style = space
indent_size = 4
insert_final_newline = true
trim_trailing_whitespace = true
end_of_line = lf
charset = utf-8

# Use 2 spaces for the HTML files
[*.html]
indent_size = 2

# The JSON files contain newlines inconsistently
[*.json]
indent_size = 2
insert_final_newline = ignore

[**/admin/js/vendor/**]
indent_style = ignore
indent_size = ignore

# Minified JavaScript files shouldn't be changed
[**.min.js]
indent_style = ignore
insert_final_newline = ignore

# Makefiles always use tabs for indentation
[Makefile]
indent_style = tab

# Batch files use tabs for indentation
[*.bat]
indent_style = tab

[*.yml]
indent_size = 2
```

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

### .mypy.ini

```ini
[mypy]
plugins =
    mypy_django_plugin.main

[mypy.plugins.django-stubs]
django_settings_module = "core.settings"
```

### .isort.cfg

```ini
[settings]
profile=black
```
