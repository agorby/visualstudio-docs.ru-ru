---
title: Управление окружениями и интерпретаторами Python
description: Окно окружений Python позволяет управлять глобальными и виртуальными окружениями, а также окружениями conda, установкой интерпретаторов и пакетов Python, а также назначением окружений для проектов Visual Studio.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1ba3902fde77e297148c2006f89dd61bca1e902b
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Как создавать окружения Python в Visual Studio и управлять ими

*Окружение* Python представляет собой контекст, в котором выполняется код Python. Различают глобальные, виртуальные окружения и окружения Conda. Окружение состоит из интерпретатора, библиотеки (обычно это стандартная библиотека Python) и нескольких установленных пакетов. Вместе они определяют, какие языковые конструкции и синтаксис допустимы, какие возможности операционной системы доступны и какие пакеты можно использовать.

В Visual Studio для Windows есть окно [Окружения Python](#the-python-environments-window), которое позволяет управлять окружениями и выбрать одно из них в качестве окружения по умолчанию для новых проектов. Все это мы рассмотрим в этой статье. Для каждого конкретного проекта можно выбрать определенное окружение вместо варианта по умолчанию.

**Примечание.** Если вы только начинаете работу с Python в Visual Studio, ознакомьтесь с необходимыми базовыми сведениями в следующих статьях:

- [Работа с Python в Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Установка поддержки Python в Visual Studio](installing-python-support-in-visual-studio.md)

Обратите внимание, что вы не можете управлять окружениями для кода Python, который открыт только в качестве папки с помощью команды **Файл** > **Открыть** > **Папка**. В таком случае [создайте проект Python на основе существующего кода](quickstart-01-python-in-visual-studio-project-from-existing-code.md), чтобы использовать функции окружения Visual Studio.

Если вы хотите установить пакеты в окружении, см. сведения о [вкладке "Пакеты"](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Типы окружений

### <a name="global-environments"></a>Глобальные среды

Каждая установка Python (например, Python 2.7, Python 3.6, Anaconda 4.4.0 и т. п.) поддерживает собственное окружение. Дополнительные сведения см. в статье [о выборе и установке интерпретаторов Python](installing-python-interpreters.md). Каждое окружение состоит из определенного интерпретатора Python, его стандартной библиотеки и набора предварительно установленных пакетов. Установив пакет в глобальном окружении, мы предоставляем к нему доступ для всех проектов, в которых оно используется. Если окружение находится в защищенной области файловой системы (например, в `c:\program files`), для установки пакетов требуются привилегии администратора.

Глобальные окружения доступны для всех проектов на компьютере. В Visual Studio вы можете выбрать одно глобальное окружение по умолчанию, которое будет использоваться для всех проектов, если вы не укажете другое для определенного проекта. Дополнительные сведения см. в разделе о [выборе окружения для проекта](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Виртуальные среды

Пакеты, установленные в глобальном окружении, доступны для всех проектов, в которых оно используется. При этом могут возникать конфликты, если двум проектам требуются несовместимые пакеты или разные версии одного пакета. Виртуальные окружения позволяют избежать таких конфликтов. В них применяются интерпретатор и стандартная библиотека из глобального окружения, но раздельные хранилища пакетов в изолированных папках.

В Visual Studio вы можете создать для конкретного проекта виртуальное окружение, которое хранится во вложенной папке проекта. В Visual Studio есть команда для создания файла `requirements.txt` из виртуального окружения, что позволяет легко воссоздать окружение на других компьютерах. См. дополнительные сведения о [виртуальных окружениях](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Окружения Conda

Окружение conda создается с помощью средства `conda` или интегрированного управления conda в Visual Studio 2017 версии 15.7 и более поздних версий. (Требуется Anaconda или Miniconda; Anaconda можно установить через установщик Visual Studio, см. раздел [Установка — Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

> [!Note]
> Для оптимальной работы с окружениями conda используйте conda 4.4.8 или более поздней версии (версии conda отличаются от версий Anaconda). Установка Anaconda 5.1 из установщика Visual Studio 2017

Чтобы просмотреть версию conda, в которой хранятся окружения conda, и другие сведения, запустите `conda info` в командной строке Anaconda (то есть в командной строке, в пути которой указана Anaconda):

```bash
conda info
```
Папки окружения conda будут выглядеть следующим образом:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Поскольку окружения conda не хранятся в проекте, они работают как глобальные среды. Например, если установить пакет в окружении Conda, он станет доступным для всех проектов, в которых используется это окружение.

Для Visual Studio 2017 версии 15.6 и более ранних версий можно использовать окружения conda, указав на них вручную, как описано в разделе [Указание существующего окружения вручную](#manually-identify-an-existing-environment).

Visual Studio 2017 версии 15.7 и более поздних версий обнаруживает окружения conda автоматически и отображает их в окне **Окружения Python**, как описано в следующем разделе.

## <a name="the-python-environments-window"></a>Окно "Окружения Python"

Окружения, обнаруженные Visual Studio, отображаются в окне **Окружения Python**. Чтобы открыть это окно, используйте один из следующих методов:

- Выберите команду меню **Просмотр** > **Другие окна** > **Окружения Python**.
- В обозревателе решений щелкните правой кнопкой мыши узел **Окружения Python** в нужном проекте и выберите **Просмотреть все окружения Python**.

    ![Команда View All Python Environments (Показать все среды Python) в обозревателе решений](media/environments-view-all.png)

В любом случае окно **Окружения Python** откроется на вкладке того же уровня, что и обозреватель решений.

![Окно со средами Python](media/environments-default-view.png)

Для всех новых проектов Visual Studio использует выделенное окружение по умолчанию, то есть Python 3.6. По умолчанию можно использовать любое из перечисленных окружений любого типа.

Команды в нижней части окна относятся к выбранному интерпретатору, и в нашем примере это установка в каталоге `C:\Python36-32` (выделенное окружение по умолчанию входит в установку Anaconda). Если нужное окружение не отображается, ознакомьтесь с разделом [Указание существующего окружения вручную](#manually-identify-an-existing-environment).

Справа от каждого окружения в списке есть элемент управления, который позволяет открыть интерактивное окно для этого окружения. (В Visual Studio 2017 15.5 и более ранних версий также может отображаться еще один элемент управления, отвечающий за обновление базы данных IntelliSense для этого окружения. Дополнительные сведения о базе данных см. в разделе [Руководство по окну окружений](python-environments-window-tab-reference.md#intellisense-tab).)

Под списком окружений есть раскрывающийся список с параметрами **Обзор**, **Пакеты** и **IntelliSense**. Они описаны в [справочной документации об окне "Окружения Python"](python-environments-window-tab-reference.md). Кроме того, если окно **Окружения Python** развернуть достаточно широко, эти параметры отобразятся в виде вкладок. Такой вариант может оказаться для вас более удобным.

![Развернутое окно Python Environments (Среды Python)](media/environments-expanded-view.png)

На рисунке выше вы видите полный список доступных окружений на этом компьютере, а также дополнительные команды для создания окружений.

> [!Note]
> Несмотря на то что Visual Studio учитывает параметр system-site-packages, его нельзя изменить из среды Visual Studio.

|   |   |
|---|---|
| ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео") | [Просмотрите видео (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) об окружениях Python в Visual Studio (2 мин 35 с).|

### <a name="what-if-no-environments-appear"></a>Что делать, если окружения не отображаются?

Если окружения не отображаются, значит Visual Studio не удалось обнаружить ни одной установки Python в стандартных расположениях. Такое может случиться, если после установки Visual Studio 2017 вы очистили все параметры интерпретаторов в настройках установщика для рабочей нагрузки Python. Возможно, вы не установили интерпретатор для Visual Studio 2015 или более ранней версии. Дополнительные сведения см. в статье [Установка интерпретаторов Python](installing-python-interpreters.md).

Если вы точно знаете, что на компьютере установлен интерпретатор Python, но Visual Studio (любая версия) не может его обнаружить, укажите его расположение вручную с помощью команды **+ Настраиваемый...** Дополнительные сведения см. в следующем разделе [Указание существующего окружения вручную](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio обнаруживает обновления для существующих интерпретаторов, например обновление Python 2.7.11 до версии 2.7.14, с помощью установщиков с сайта python.org. В процессе установки старое окружение исчезнет из списка **Окружения Python**, прежде чем на его месте появится обновленная версия.
>
> Но если вы переместите интерпретатор и его окружение вручную с помощью средств файловой системы, Visual Studio не сможет узнать его новое расположение. Дополнительные сведения см. в разделе [о перемещении интерпретатора](installing-python-interpreters.md#moving-an-interpreter).

<a name="manually-identifying-an-existing-environment></a>

## <a name="manually-identify-an-existing-environment"></a>Указание существующего окружения вручную

Чтобы указать окружение (в том числе окружение Conda в Visual Studio 2017 версии 15.6 и более ранних версий), установленное в нестандартном расположении, выполните следующие действия:

1. Выберите **+ Настраиваемое** в окне **Окружения Python**, чтобы открыть вкладку **Настройка**:

    ![Представление по умолчанию для новой настраиваемой среды](media/environments-custom-1.png)

1. Введите имя среды в поле **Описание**.

1. Введите путь к интерпретатору или найдите его (с помощью кнопки **...***) в поле **Префикс пути**.

1. Если Visual Studio обнаружит интерпретатор Python в этом расположении (ниже представлен пример пути к окружению Conda), команда **Автоматическое определение** станет активна. Если выбрать **Автоматическое определение*, все оставшиеся поля заполняется автоматически. Также вы можете заполнить эти поля вручную.

    ![Включение команды автоматического определения](media/environments-custom-2.png)

    ![Заполнение полей сведениями об окружении с помощью автоматического определения](media/environments-custom-3.png)

1. Когда все поля будут заполнены нужными значениями, щелкните **Применить**, чтобы сохранить конфигурацию. Теперь это окружение можно использовать в Visual Studio так же, как и остальные.

1. Если потребуется удалить окружение, которое вы указали вручную, щелкните команду **Удалить** на вкладке **Настройка**. Для автоматически обнаруженных сред этот параметр не предлагается. Дополнительные сведения см. в [описании вкладки "Настройка"](python-environments-window-tab-reference.md#configure-tab).

## <a name="create-a-conda-environment"></a>Создание окружения conda

*Visual Studio 2017 версии 15.7 и более поздней.*

1. Выберите **+ Создать окружение conda** в окне **Окружения Python**, чтобы открыть вкладку **Создать новое окружение conda**:

    ![Создание вкладки для нового окружения conda](media/environments-conda-1.png)

1. Введите имя окружения в поле **Имя**, выберите базовый интерпретатор Python в поле **Python** и нажмите **Создать**.

1. В окне **Вывод** отображается ход выполнения для нового окружения с несколькими инструкциями CLI после завершения создания:

    ![Успешное создание окружения conda](media/environments-conda-2.png)

1. В Visual Studio можно активировать окружение conda для проекта так же, как любое другое окружение, как описано в статье [Выбор окружения для проекта](selecting-a-python-environment-for-a-project.md).

1. Установить пакеты в окружении можно на вкладке [Пакеты](python-environments-window-tab-reference.md#packages-tab).

## <a name="see-also"></a>См. также

- [Установка интерпретаторов Python](installing-python-interpreters.md)
- [Выбор интерпретатора для проекта](selecting-a-python-environment-for-a-project.md)
- [Использование requirements.txt для зависимостей](managing-required-packages-with-requirements-txt.md)
- [Пути поиска](search-paths.md)
- [Справочная информация по окну "Окружения Python"](python-environments-window-tab-reference.md)