---
title: "Опубликовать в службе приложений Azure — Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c1fa8867c4f9ab46b50f0b2a144970d772cbd71
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2017
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Публикация приложений ASP.NET или ASP.NET Core для службы приложений Azure с помощью Visual Studio

Можно использовать **публикации** средство для публикации приложений ASP.NET, ASP.NET Core, Python, Node.js и .NET Core в службе приложений Azure.

Если вы еще нет учетной записи Azure, вы можете [регистрации здесь](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio выберите **файл > Новый проект**.

1. В разделе **Visual C#** или **Visual Basic**, выберите **Web**, а затем в средней области выберите **веб-приложения ASP.NET (.NET Framework)**(только C#) или **веб-приложения ASP.NET Core**, а затем нажмите кнопку **ОК**.

1. Выберите **MVC**, убедитесь, что **без проверки подлинности** выбран и нажмите кнопку **ОК**.

1. Введите имя, например **MyWebApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

1. Выберите **сборки > построить решение** для сборки проекта.

## <a name="publish-to-azure-app-service"></a>Публикация в службу приложений Azure

1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите команду **публикации**.

    ![Выберите опубликовать](../deployment/media/quickstart-publish-aspnet.png "выберите публикации")

1. В **публикации** области, выберите **службу приложений Microsoft Azure**.

    ![Выберите службы приложений Azure](../deployment/media/quickstart-publish-azure.png "выберите службы приложений Azure")

1. Нажмите кнопку **Опубликовать**.

    **Создание приложения службы** откроется диалоговое окно.

    ![Создание приложения службы](../deployment/media/quickstart-publish-settings-app-service.png "создания службы приложений Azure")
    
1. Если вы не вошли в Visual Studio, войдите и заполните поля параметров по умолчанию приложение службы.

    Профиль публикации, параметры, откроется диалоговое окно.

    ![Выберите папку](../deployment/media/quickstart-publish-settings-web.png "выберите папку")

    В этом диалоговом окне можно выберите подписку, которую вы используете, выбрать или создать группы ресурсов Azure и т. д.

1. Нажмите кнопку **Создать**.

    Visual Studio развертывает приложение в службе приложений Azure, и загружает веб-приложения в браузере.

    В сводке **публикации** панели отображается URL-адрес сайта для новой службы приложения Azure.

## <a name="next-steps"></a>Следующие шаги

- [Развертывание приложения ASP.NET Core в Azure](https://docs.microsoft.com/en-us/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Непрерывное развертывание ASP.NET Core в Azure с помощью Git](https://docs.microsoft.com/en-us/aspnet/core/publishing/azure-continuous-deployment)