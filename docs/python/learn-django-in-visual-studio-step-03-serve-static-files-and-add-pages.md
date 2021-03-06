---
title: Руководство. Сведения о Django в Visual Studio (шаг 3)
description: Пошаговое руководство по основам Django в контексте проектов Visual Studio, в частности демонстрация обработки статических файлов, добавление страниц в приложение и использование наследования шаблонов
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: b267c4963eede53f433bd929eb7944ad53e9a8ba
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="tutorial-step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Руководство (шаг 3). Обработка статических файлов, добавление страниц и использование наследования шаблонов

**Предыдущий шаг. [Руководство (шаг 2). Создание приложения Django с представлениями и шаблонами страниц](learn-django-in-visual-studio-step-02-create-an-app.md)**

В предыдущих шагах этого руководства рассматривалось создание минимального приложения Django с одной страницей автономного HTML. Современные веб-приложения обычно состоят из многих страниц и используют общие ресурсы, такие как CSS, JavaScript и файлы, для обеспечения согласованного стиля и реакции на событие.

На этом шаге вы научитесь делать следующее:

> [!div class="checklist"]
> - с помощью шаблонов элементов Visual Studio быстро создавать файлы различных типов с удобным стандартным кодом (шаг 3–1);
> - настраивать проект Django для обслуживания статических файлов (шаг 3–2);
> - добавлять дополнительные страницы в приложение (шаг 3–3);
> - использовать наследование шаблона для создания заголовка и панели навигации, которая используется на разных страницах (шаг 3–4).

## <a name="step-3-1-become-familiar-with-item-templates"></a>Шаг 3–1. Знакомство с шаблонами элементов

По мере разработки приложения Django обычно добавляется множество дополнительных файлов Python, HTML, CSS и JavaScript. Для каждого типа файла (а также других файлов, таких как `web.config`, которые могут понадобиться для развертывания) Visual Studio предоставляет удобные [шаблоны элементов](python-item-templates.md) для начала работы.

Чтобы просмотреть доступные шаблоны, перейдите к **обозревателю решений**, щелкните правой кнопкой мыши папку, в которой необходимо создать элемент, выберите **Добавить** > **Новый элемент**:

![Диалоговое окно ''Добавление нового элемента'' в Visual Studio](media/django/step03-add-new-item-dialog.png)

Чтобы использовать шаблон, выберите нужный шаблон, укажите имя файла и нажмите кнопку **ОК**. При добавлении элемента таким образом автоматически добавляется файл в проект Visual Studio и отмечает изменения для системы управления версиями.

Visual Studio также добавляет некоторые часто используемые параметры для меню **Добавить** напрямую. Например, в проекте Python есть команды **HTML-страница** или **Таблица стилей** в нижней части меню **Добавить**, которые запрашивают ввод имени и создают файл.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Вопрос. Как Visual Studio знает, какой шаблон элемента предложить?

Ответ. Файл проекта Visual Studio (`.pyproj`) содержит идентификатор типа проекта, который помечает его как проект Python. Visual Studio использует этот тип идентификатора для отображения шаблонов элементов, подходящих для типа проекта. Таким образом Visual Studio может предоставлять богатый набор шаблонов элементов для многих типов проектов, который не требуется отсортировывать каждый раз.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Шаг 3–2. Обработка статических файлов из приложения

В веб-приложении, созданном с помощью Python (с помощью любой платформы), файлы Python всегда выполняются на сервере веб-узла и никогда не передаются на компьютер пользователя. Однако другие файлы, такие как каскадные таблицы стилей и JavaScript, используются исключительно браузером, поэтому сервер узла просто доставляет их без изменений всякий раз, когда они запрашиваются. Такие файлы называются статическими файлами, Django может доставлять их автоматических без необходимости написания кода.

Проект Django по умолчанию настроен обрабатывать статические файлы из папки `static` приложения благодаря таким строкам в проекте Django `settings.py`:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Файлы можно организовать, используя любую предпочитаемую структуру папок в `static`, а затем использовать относительные пути в этой папке для обращения к файлам. Чтобы продемонстрировать этот процесс, на следующих шагах добавляется файл каскадных таблиц стилей в приложение, а затем эта таблица стилей используется в шаблоне `index.html`:

1. В **обозревателе решений** в проекте Visual Studio щелкните папку HelloDjangoApp правой кнопкой мыши, выберите **Добавить** > **Новая папка** и назовите папку `static`.

1. Щелкните папку `static` правой кнопкой мыши и выберите **Добавить** > **Новый элемент**. В открывшемся диалоговом окне выберите шаблон "Таблица стилей", назовите файл `site.css` и нажмите кнопку **ОК**. Файл `site.css` появится в проекте и откроется в редакторе. Структура папки должна выглядеть похоже на структуру на следующем рисунке:

    ![Структура статического файла, показанная в обозревателе решений](media/django/step03-static-file-structure.png)

1. Замените все содержимое `site.css` следующим кодом и сохраните файл:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Замените содержимое файла `templates/HelloDjangoApp/index.html` приложения следующим кодом, который заменяет элемент `<strong>`, используемый на шаге 2, элементом `<span>`, ссылающимся на класс стиля `message`. Использование класса стиля таким образом дает большую гибкость в стилизации элемента. (Если вы не переместили `index.html` в подпапку в `templates`, ознакомьтесь со сведениями об [организации пространства имен шаблонов](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) на шаге 2.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Запустите проект для просмотра результатов. Остановите сервер после выполнения и зафиксируйте изменения в системе управления версиями, если это необходимо (как описано на [шаге 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-purpose-of-the--load-staticfiles--tag"></a>Вопрос. Какое назначение у тега {% load staticfiles %}?

Ответ. Строка `{% load staticfiles %}` необходима для ссылки на статические файлы в таких элементах, как `<head>` и `<body>`. В примере, показанном в этом разделе, staticfiles ссылается на пользовательский набор тегов шаблона Django, который позволяет использовать синтаксис `{% static %}` для ссылки на статические файлы.  Без `{% load staticfiles %}` при выполнении приложения отобразится исключение.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Вопрос. Существуют ли соглашения для организации статических файлов?

Ответ. Вы можете добавить другие файлы CSS, JavaScript и HTML в свою папку `static` любым способом. Типичный способ организации статических файлов — это создание подпапок под названием `fonts`, `scripts` и `content` (для таблиц стилей и других файлов). В каждом случае не забудьте включить эти папки в относительный путь к файлу в ссылках `{% static %}`.

## <a name="step-3-3-add-a-page-to-the-app"></a>Шаг 3–3. Добавление страницы в приложение

Добавление еще одной страницы в приложение означает:

- добавление функции Python, которая определяет представление;
- добавление шаблона для исправления страницы;
- добавление необходимой маршрутизации в файл `urls.py` проекта Django.

Следующие действия добавляются на странице "Дополнительные сведения" проекта HelloDjangoApp и связывают эту страницу с домашней страницей:

1. В **обозревателе решений** щелкните правой кнопкой мыши папку `templates/HelloDjangoApp`, выберите **Добавить** > **Новый элемент**, щелкните шаблон элемента "HTML-страница", назовите файл `about.html` и нажмите кнопку **ОК**.

    > [!Tip]
    > Если команда **Новый элемент** не появляется в меню **Добавить**, убедитесь, что вы остановили сервер, чтобы служба Visual Studio вышла из режима отладки.

1. Замените содержимое `about.html` следующим исправлением (вы замените явную ссылку на домашнюю страницу простой навигационной панелью на шаге 3–4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Откройте файл `views.py` приложения и добавьте функцию с именем `about`, которая использует шаблон:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Откройте файл `urls.py` проекта Django и добавьте следующую строку в массив `urlPatterns`:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Откройте файл `templates/HelloDjangoApp/index.html` и добавьте следующую линию под элементом `<body>`, чтобы связать страницу дополнительных сведений (опять же, вы заменяете эту ссылку навигационной панелью на шаге 3–4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Сохраните все файлы с помощью команды меню **Файл** > **Сохранить все** или просто нажмите CTRL+SHIFT+S. (Технически этот шаг не требуется, так как при запуске проекта в Visual Studio файлы автоматически сохраняются. Однако об этой команде лучше знать.)

1. Выполните проект, чтобы просмотреть результаты и проверьте перемещение по страницам. Закройте сервер после завершения.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Вопрос. Я пытался использовать index для связи с домашней страницей, но он не работает. Почему?

Ответ. Не смотря на то, что функция представления в `views.py` называется `index`, шаблоны маршрутизации URL-адресов в файле `urls.py` проекта Django не содержат регулярных выражений, которые совпадают со строкой index. Чтобы сопоставить эту строку, необходимо добавить еще одну запись для шаблона `^index$`.

Как показано в следующем разделе, лучше использовать тег `{% url '<pattern_name>' %}` в шаблоне страницы, чтобы ссылаться на *имя* шаблона. В этом случае Django создаст соответствующий URL-адрес. Например, замените `<div><a href="home">Home</a></div>` в `about.html` на `<div><a href="{% url 'index' %}">Home</a></div>`. Использование index работает, потому что первый шаблон URL-адреса в `urls.py` называется index (из-за аргумента `name='index'`). Вы также можете использовать home для обозначения второго шаблона.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Шаг 3–4. Использование наследования шаблона для создания заголовка и навигационной панели

Вместо создания явных навигационных ссылок на каждой странице современные веб-приложения обычно используют заголовок фирменной символики и панель навигации, которая предоставляет самые важные ссылки на страницы, всплывающие меню и т. д. Убедитесь, что заголовок и навигационная панель одинаковы на всех страницах, но не повторяйте один и тот же код в каждом шаблоне страницы. Вместо этого необходимо определить общие компоненты всех страниц в одном месте.

Система шаблонов Django предоставляет два способа повторного использования определенных элементов в нескольких шаблонах: включение и наследование.

- *Включение*. Это другие шаблоны страниц, которые вставляются в определенное место в ссылочном шаблоне, используя синтаксис `{% include <template_path> %}`. Кроме того, можно использовать переменную, если необходимо динамически изменять путь в коде. Включение обычно используется в тексте страницы для извлечения общего шаблона в определенном расположении на странице.

- *Наследование*. В начале шаблона страницы используется `{% extends <template_path> %}` для определения общего базового шаблона, на основе которого затем создается ссылочный шаблон. Наследование обычно используется для определения общего макета, навигационной панели и других структур для страниц приложения, так что ссылочным шаблонам необходимо только добавлять или изменять определенные области базового шаблона, называемые *блоками*.

В обоих случаях `<template_path>` относится к папке `templates` приложения (`../` или `./` также разрешены).

Базовый шаблон отделяет блоки с помощью тегов `{% block <block_name> %}` и `{% endblock %}`. Если ссылочный шаблон использует теги с тем же именем блока, содержимое блока перезаписывает содержимое базового шаблона.

Далее демонстрируется наследование:

1. В папке `templates/HelloDjangoApp` приложения создайте HTML-файл (с помощью контекстного меню **Добавить** > **Новый элемент** или **Добавить** > **HTML-страница**) под названием `layout.html` и вставьте в него указанное ниже содержимое. Вы увидите, что этот шаблон содержит блок под названием content, который должен быть заменен для всех ссылающихся страниц:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Добавьте следующие стили в файл `static/site.css` приложения (в этом пошаговом руководстве мы не пытаемся продемонстрировать гибкость дизайна, эти стили просто позволяют получить интересные результаты):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Измените `templates/HelloDjangoApp/index.html` для ссылки на базовый шаблон и перезаписи блока content. Можно увидеть, что с помощью наследования этот шаблон упрощается:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Измените `templates/HelloDjangoApp/about.html`, чтобы ссылаться на базовый шаблон и перезаписать блок content:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Запустите сервер для просмотра результатов. Закройте сервер после завершения.

    ![Выполнение приложения, показывающего панель навигации](media/django/step03-nav-bar.png)

1. Так как в приложение были внесены значительные изменения, самое время [зафиксировать изменения в системе управления версиями](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Tutorial step 4: Use the full Django Web Project template](learn-django-in-visual-studio-step-04-full-django-project-template.md) (Руководство (шаг 4). Использование полного шаблона веб-проекта Django)

## <a name="going-deeper"></a>Дополнительные сведения

- [Writing your first Django app, part 3](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (Написание первого приложения Django (часть 3)) (docs.djangoproject.com)
- Дополнительные сведения о возможностях шаблонов Django, таких как поток управления, см. в статье [The Django template language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (Язык шаблона Django) (docs.djangoproject.com).
- Подробные сведения об использовании тега `{% url %}` см. в разделе [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) в статье [Built-in template tags and filters for Django templates reference](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (Встроенные теги и фильтры шаблонов для ссылки на шаблоны Django) (docs.djangoproject.com).
- Руководство по исходному коду на сайте GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)