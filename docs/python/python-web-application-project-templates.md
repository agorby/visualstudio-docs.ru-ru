---
title: Шаблоны веб-приложений для Python
description: Обзор шаблонов Visual Studio для веб-приложений, написанных на языке Python с помощью платформ Bottle, Flask и Django, включая конфигурации отладки и публикацию в службе приложений Azure.
ms.date: 04/17/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 6d76bc7868c78b1def09376cb2382aa39cff1cda
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
# <a name="python-web-application-project-templates"></a>Шаблоны проекта веб-приложений Python

Python в Visual Studio поддерживает разработку веб-проектов на платформах Bottle, Django и Flask с помощью шаблонов проектов и средства запуска отладки, которое можно настроить для работы с различными платформами. Эти шаблоны включают файл `requirements.txt` для объявления необходимых зависимостей. При создании проекта на основе одного из таких шаблонов в Visual Studio отобразится запрос на установку этих пакетов (см. раздел [Установка необходимых компонентов для проекта](#installing-project-requirements) далее в этой статье).

Для других платформ, например Pyramid, вы также может использовать универсальный шаблон веб-проекта. В этом случае для шаблона не предусмотрена установка каких-либо платформ. Вместо этого в окружении проекта устанавливаются необходимые пакеты (см. статью об [управлении окружениями Python](managing-python-environments-in-visual-studio.md)).

## <a name="using-a-project-template"></a>Использование шаблона проекта

Чтобы создать проект на основе шаблона, последовательно выберите **Файл** > **Создать** > **Проект**. Чтобы просмотреть шаблоны для веб-проектов, слева в диалоговом окне последовательно выберите **Python** > **Интернет**. Выберите шаблон по своему усмотрению, присвоив имена проекту и решению. Затем задайте параметры для каталога решения и репозитория Git и нажмите кнопку **ОК**.

![Диалоговое окно "Новый проект" веб-приложений](media/projects-new-project-dialog-web.png)

Универсальный шаблон "Веб-проект", который упоминался ранее, содержит пустой проект Visual Studio без кода (подразумевается только проект Python). Сведения о шаблоне "Облачная служба Azure" см. в статье [Проекты облачных служб Azure для Python](python-azure-cloud-service-project-template.md) (python-azure-cloud-service-project-template.md).

Все другие шаблоны основаны на веб-платформах Bottle, Flask или Django и делятся на три общие группы, как описано в следующих разделах. Приложения, созданные с помощью любого из этих шаблонов, содержат код, который обеспечивает локальное выполнение и отладку приложений. Кроме того, каждый из них предоставляет необходимый [объект приложения WSGI](http://www.python.org/dev/peps/pep-3333/) (python.org) для [развертывания в Службе приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

### <a name="blank-group"></a>Пустая группа

С помощью всех шаблонов пустых веб-проектов для конкретных платформ создаются проекты с использованием большего или меньшего объема стандартного кода и необходимых зависимостей, объявленных в файле `requirements.txt`.

| Шаблон | Описание: |
| --- | --- |
| Пустой веб-проект Bottle | В `app.py` создается минимальное приложение с домашней страницей для `/` и страницей `/hello/<name>`, на которой выводится `<name>`. Используется небольшой встроенный шаблон. |
| Пустой веб-проект Django | Создается проект Django с основной структурой веб-сайта Django, но без структуры приложений Django. Дополнительные сведения см. в статье о [шаблонах Django](python-django-web-application-project-template.md) и [шаге 1 руководства по изучению Django](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| Пустой веб-проект Flask | Создается минимальное приложение для вывода одной страницы "Hello World!" для `/`. Это приложение похоже на результат выполнения инструкций в [кратком руководстве по созданию первого веб-приложения Python с помощью Visual Studio](../ide/quickstart-python.md?context=visualstudio/python/default).

### <a name="web-group"></a>Веб-группа

С помощью всех шаблонов веб-проектов для конкретных платформ создаются начальные веб-приложения с идентичной конструкцией, независимо от выбранной платформы. В приложении есть домашняя страница, страницы со сведениями и контактными данными, а также панель навигации и адаптивный макет, созданный на основе Bootstrap. Все приложения соответствующим образом настроены для статических файлов сервера (CSS, JavaScript и шрифты). Используется механизм шаблона страницы, соответствующий конкретной платформе.

| Шаблон | Описание: |
| --- | --- |
| Веб-проект Bottle | Создается приложение, статические файлы которого содержатся в папке `static` и обрабатываются с помощью кода в `app.py`. Данные маршрутизации для отдельных страниц содержатся в `routes.py`, а шаблоны страниц — в папке `views`.|
| Веб-проект Django | Создается проект и приложение Django с тремя страницами, поддержкой аутентификации и базой данных SQLite (без моделей данных). Дополнительные сведения см. в статье о [шаблонах Django](python-django-web-application-project-template.md) и [шаге 4 руководства по изучению Django](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| Веб-проект Flask | Создается приложение, статические файлы которого содержатся в папке `static`. Маршрутизация обрабатывается с помощью кода в `views.py`. Шаблоны страниц, созданные с использованием механизма Jinja, содержатся в папке `templates`. Код запуска помещен в файл `runserver.py`. |
| Веб-проект Flask и Jade | Создается то же приложение, что и при использовании шаблона "Веб-проект Flask", но с помощью модуля создания шаблонов Jade. |

### <a name="polls-group"></a>Группа опроса

С помощью шаблонов веб-проектов опроса для конкретных платформ создаются начальные веб-приложения, в которых пользователи смогут пройти опрос. Каждое приложение основано на структуре шаблона веб-проекта, которая позволяет использовать базу данных для управления опросами и ответами пользователей. Эти приложения включают соответствующие модели данных и специальную страницу приложения ("/seed"), с помощью которой из файла `samples.json` загружается опрос.

| Шаблон | Описание: |
| --- | --- |
| Веб-проект опроса Bottle | Создается приложение, которое можно запустить с выполняющейся в памяти базой данных, MongoDB или службой "Хранилище таблиц Azure", которая настраивается с помощью переменной среды `REPOSITORY_NAME`. Модели данных и код хранилища данных содержатся в папке `models`. В файл `settings.py` помещен код, который определяет используемое хранилище данных. |
| Веб-проект опроса Django | Создаются проект и приложение Django с тремя страницами и базой данных SQLite. Шаблон включает настройки в интерфейсе администратора Django, которые позволяют прошедшему аутентификацию администратору создавать опросы и управлять ими. Дополнительные сведения см. в статье о [шаблонах Django](python-django-web-application-project-template.md) и [шаге 6 руководства по изучению Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| Веб-проект опроса Flask | Создается приложение, которое можно запустить с выполняющейся в памяти базой данных, MongoDB или службой "Хранилище таблиц Azure", которая настраивается с помощью переменной среды `REPOSITORY_NAME`. Модели данных и код хранилища данных содержатся в папке `models`. В файл `settings.py` помещен код, который определяет используемое хранилище данных. В приложении применяется модуль Jinja для создания шаблонов страниц. |
| Веб-проект опроса Flask и Jade | Создается то же приложение, что и при использовании шаблона "Веб-проект опроса Flask", но с использованием модуля Jade для создания шаблонов. |

## <a name="installing-project-requirements"></a>Установка необходимых компонентов для проекта

При создании проекта из шаблона для конкретной платформы отображается диалоговое окно для установки необходимых пакетов с помощью pip. Чтобы при публикации веб-сайта были настроены правильные зависимости, для веб-проектов рекомендуется использовать [виртуальную среду](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

![Диалоговое окно, с помощью которого можно установить необходимые пакеты для шаблона проекта](media/template-web-requirements-txt-wizard.png)

Если используется система управления версиями, папка виртуального окружения обычно опускается, так как виртуальное окружение можно воссоздать только с помощью `requirements.txt`. Чтобы исключить папку, рекомендуем сначала выбрать вариант **самостоятельной установки**, показанный выше в окне с запросом, а затем отключить автоматическую фиксацию перед созданием виртуального окружения. Дополнительные сведения см. в [шагах 1.2. и 1.3. руководства по изучению Django](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Выполняя развертывание в службе приложений Microsoft Azure, нужно выбрать версию Python в качестве [расширения сайта](https://aka.ms/PythonOnAppService) и установить пакеты вручную. Кроме того, поскольку при развертывании из Visual Studio служба приложений Azure **не** устанавливает пакеты из файла `requirements.txt` автоматически, используйте сведения о конфигурации, указанные в статье [Upgrading Python on Azure App Service](https://aka.ms/PythonOnAppService) (Обновление Python в службе приложений Azure).

Облачные службы Microsoft Azure *поддерживают* файл `requirements.txt`. Дополнительные сведения см. в статье [Проекты облачных служб Azure для Python](python-azure-cloud-service-project-template.md).

## <a name="debugging"></a>Отладка

Когда вы запускаете отладку веб-проекта, Visual Studio запускает локальный веб-сервер со случайным портом и открывает страницу с указанным здесь адресом и портом в браузере по умолчанию. Чтобы указать дополнительные параметры, щелкните правой кнопкой мыши проект, выберите **Свойства** и откройте вкладку **Веб-средство запуска**:

![Свойства веб-средства запуска для универсального веб-шаблона](media/template-web-launcher-properties.png)

Параметры группы **Отладка**:

- Параметры **Пути поиска**, **Аргументы сценария**, **Аргументы интерпретатора** и **Путь к интерпретатору** ничем не отличаются от используемых в режиме [обычной отладки](debugging-python-in-visual-studio.md).
- **URL-адрес для запуска** — задает URL-адрес, который открывается в браузере. По умолчанию для него используется значение `localhost`.
- **Номер порта.**  Это порт, который будет использоваться, если в URL-адресе не указан порт (по умолчанию Visual Studio автоматически выбирает порт). Этот параметр позволяет переопределить значение по умолчанию переменной среды `SERVER_PORT`, которое используется шаблонами для настройки порта, прослушиваемого локальным сервером отладки.

Свойства, указанные в группах **команды запуска сервера** и **команды отладки сервера** (последняя группа находится ниже в окне, показанном на рисунке), определяют, как будет запускаться веб-сервер. Так как для многих платформ требуется использовать сценарий вне текущего проекта, можно настроить сценарий здесь и передать модуль автозагрузки как параметр.

- **Команда** — может содержать сценарий Python (файл `*.py`), имя модуля (как и в `python.exe -m module_name`) или одну строку кода (как и в `python.exe -c "code"`). Значение в раскрывающемся списке указывает, какой из этих типов будет использоваться.
- **Аргументы** — содержимое этого поля передается в командной строке после команды.
- **Среда** — разделенный символом новой строки список пар `NAME=VALUE`, определяющих переменные среды. Эти переменные задаются после всех свойств, которые могут изменить среду, например номер порта или пути поиска, и поэтому могут перезаписать эти значения.

Любое свойство проекта и любую переменную среды можно указать, используя синтаксис MSBuild, например `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` — это относительный путь к файлу запуска, а `{StartupModule}` — импортируемое имя файла запуска. `$(SERVER_HOST)` и `$(SERVER_PORT)` являются обычными переменными среды, автоматически задаваемые свойствами **URL-адрес для запуска** и **Номер порта** или с помощью свойства **Среда**.

> [!Note]
> Значения в группе **команды запуска сервера** используются при выборе команды **Отладка > Start Server (Запуск сервера)** или нажатии клавиш CTR+F5. Значения в группе **команды отладки сервера** используются при выборе команды **Отладка > Start Debug Server (Запустить сервер отладки)** или нажатии клавиши F5.

### <a name="sample-bottle-configuration"></a>Пример конфигурации Bottle

Шаблон **веб-проекта Bottle** содержит стандартный код, который выполняет необходимую настройку. Импортированное приложение Bottle может не содержать этот код, однако в этом случае следующие параметры запускают приложение с помощью установленного модуля `bottle`:

- Группа **команды запуска сервера**:
  - **Команда**: `bottle` (модуль);
  - **Аргументы**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`.

- Группа **команды отладки сервера**:
  - **Команда**: `bottle` (модуль);
  - **Аргументы**: `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`.

При отладке с помощью Visual Studio мы не рекомендуем использовать параметр `--reload`.

### <a name="sample-pyramid-configuration"></a>Пример конфигурации приложения Pyramid

В настоящее время для создания приложений Pyramid лучше всего использовать средство командной строки `pcreate`. После создания приложения его можно импортировать с помощью шаблона [На основе существующего кода Python](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files). Затем настройте параметры в свойствах **универсального веб-проекта**. Эти параметры предполагают, что платформа Pyramid установлена в виртуальной среде в `..\env`.

- Группа **отладки**:
  - **Порт сервера**: 6543 (или заданный в INI-файлах).

- Группа **команды запуска сервера**:
  - Команда: `..\env\scripts\pserve-script.py` (сценарий);
  - Аргументы: `Production.ini`

- Группа **команды отладки сервера**:
  - Команда: `..\env\scripts\pserve-script.py` (сценарий);
  - Аргументы: `Development.ini`

> [!Tip]
> Скорее всего, потребуется настроить свойство **Рабочий каталог** проекта, так как приложения Pyramid обычно находятся в папке на один уровень ниже корневого каталога проекта.

### <a name="other-configurations"></a>Другие конфигурации

Если у вас есть параметры для другой платформы, которыми вы хотите поделиться, или вы хотите запросить параметры для такой платформы, откройте обращение в [репозитории GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Преобразование проекта в проект облачной службы Azure

С помощью команды **Преобразовать в проект облачной службы Microsoft Azure** (см. рисунок ниже) можно добавить проект облачной службы в решение. Этот проект включает параметры развертывания и конфигурации для используемых виртуальных машин и служб. Используйте команду **Опубликовать** в облачном проекте, чтобы выполнить развертывание в облачных службах. С помощью команды **Опубликовать** в проекте Python можно по-прежнему выполнить развертывание на веб-сайтах. Дополнительные сведения см. в статье [Проекты облачных служб Azure для Python](python-azure-cloud-service-project-template.md).

![Команда "Преобразовать в проект облачной службы Microsoft Azure"](media/template-web-convert-menu.png)

## <a name="see-also"></a>См. также

- [Справочник по шаблонам элементов Python](python-item-templates.md)
- [Публикация в службу приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
