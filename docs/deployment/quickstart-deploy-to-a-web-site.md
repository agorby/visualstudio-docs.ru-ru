---
title: Опубликовать на веб-сайт - Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f722dcc4ada5643f9de3342b85469fa667d4b7c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766556"
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Публикация веб-приложения или приложения .NET Core на веб-сайт, используя средство публикации Visual Studio

Можно использовать **публикации** средство для публикации приложения ASP.NET на веб-сайт.

Эти шаги применимы к ASP.NET, ASP.NET Core, .NET Core и Python приложений в Visual Studio. Для Node.js действия поддерживаются, но пользовательский интерфейс отличается.

## <a name="prerequisites"></a>Предварительные требования

* Необходимо иметь Visual Studio 2017 г. установлен и **ASP.NET и веб-разработки** рабочей нагрузки и. **NET разработки настольных приложений** рабочей нагрузки. Для приложения .NET Core, необходим. **NET Core** рабочей нагрузки.

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio последовательно выберите **Файл > Создать проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

1. Выберите **MVC** (или выберите **веб-приложения (Model-View-Controller)** для .NET Core), убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК** .

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="publish-to-a-web-site"></a>Опубликовать на веб-сайт

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать**.

    ![Выберите опубликовать](../deployment/media/quickstart-publish-aspnet.png "выберите публикации")

1. Если были настроены ранее все профили публикации **публикации** появится область. Нажмите кнопку **Создание нового профиля**.

1. В **выбрать место назначения публикации** диалогового окна выберите **IIS, FTP, и т. д**.

    ![Выберите IIS, FTP, т. д.](../deployment/media/quickstart-publish-iis-ftp.png "выберите IIS, FTP и т. д.")

1. Нажмите кнопку **Опубликовать**.

    Профиль публикации, параметры, откроется диалоговое окно.

    ![Выберите папку](../deployment/media/quickstart-publish-settings-web.png "выберите папку")

1. В **метод публикации** поля, такие как выбрать метод **веб-развертывания** или **FTP**.

    Параметры, которые вы видите рядом соответствуют способа публикации. Веб-развертывания упрощает развертывание веб-приложений и веб-сайтов на серверах IIS, а также должен быть установлен как приложение на сервере. Используйте [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) для ее установки.

1. Настроить необходимые параметры для метода публикации и нажмите кнопку **проверить подключение**.

    Если сервер или целевой доступен, и все настройки указаны правильно, вы увидите сообщение, которое указывает соединение, которое проверяется, и вы готовы к публикации.

    ![Проверка подключения к](../deployment/media/quickstart-publish-web-deploy.png "Проверка подключения к")

1. Если вы хотите настроить другие параметры развертывания, нажмите кнопку **параметры**.

    Можно настроить параметры, как развернуть конфигурацию отладки или выпуска, а затем нажмите кнопку **Сохранить**. При удаленной отладке конфигурации отладки является обязательным.

1. Чтобы опубликовать, нажмите кнопку **публикации**.

    В окне вывода отображаются ход выполнения развертывания и результатов.

## <a name="next-steps"></a>Следующие шаги

В этом кратком руководстве вы узнали, как использовать Visual Studio для создания профиля публикации. Вы можете также настроить публикацию профиля путем импорта параметров публикации.

> [!div class="nextstepaction"]
> [Импорт параметров публикации и развертывание в IIS](tutorial-import-publish-settings-iis.md)
