---
title: Удаленная отладки ASP.NET Core для служб IIS и Azure | Документы Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: a4e03f9a369959a5736d7030a1dac885771d7984
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746771"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Удаленная отладка ASP.NET Core на сервере IIS в Azure в Visual Studio 2017 г.

В этом руководстве объясняется, как установить и настроить приложение ASP.NET Core Visual Studio 2017 г., развернуть его в службах IIS с помощью Azure и присоединить удаленный отладчик из Visual Studio.

Способ, рекомендуемый для удаленной отладки в Azure зависит от сценария:

* Отладке ASP.NET Core в службе приложений Azure см. в разделе [отладки Azure приложения с помощью отладчика моментального снимка](../debugger/debug-live-azure-applications.md). Это рекомендуемый метод.
* Отладка ASP.NET Core в службе приложений Azure с помощью более традиционные возможности отладки, выполните действия, описанные в этом разделе (см. в разделе [удаленной отладки на службе приложений Azure](#remote_debug_azure_app_service)).

    В этом случае необходимо развернуть приложение из Visual Studio в Azure, но необходимо вручную установить или настроить IIS или удаленный отладчик (эти компоненты, были представлены пунктирной линией), как показано на следующем рисунке.

    ![Компоненты удаленной отладки](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Для отладки службы IIS на Виртуальной машине Azure, выполните действия, описанные в этом разделе (см. в разделе [удаленной отладки на Виртуальной машине Azure](#remote_debug_azure_vm)). Это позволяет использовать пользовательскую конфигурацию служб IIS, но действий Установка и развертывание более сложной.

    Для виртуальной Машины Azure необходимо развернуть приложение из Visual Studio в Azure, а также необходимо вручную установить роль IIS и удаленным отладчиком, как показано на следующем рисунке.

    ![Компоненты удаленной отладки](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Отладке ASP.NET Core в Azure Service Fabric см. в разделе [отладки удаленного приложения Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Не забудьте удалить ресурсы Azure, созданные после завершения действия в этом учебнике. Таким образом можно избежать дополнительной ненужных затрат.


### <a name="requirements"></a>Требования

Отладка между двумя компьютерами, подключенными через прокси-сервер не поддерживается. Отладка в различных странах через высокой задержкой или низкой пропускной способностью, таких как удаленный доступ к Интернету, либо через Интернет не рекомендуется и может произойти сбой или медленную неприемлемо. Полный список требований см. в разделе [требования](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Создание приложения ASP.NET Core на компьютере Visual Studio 2017 г. 

1. Создание нового приложения ASP.NET Core. (Выберите **файл > Создать > проект**, а затем выберите **Visual C# > Web > веб-приложения ASP.NET Core**).

    В **ASP.NET Core** шаблонов выберите пункт **веб-приложение**.

2. Убедитесь, что **ASP.NET Core 2.0** выбран, **Включение поддержки Docker** — **не** выбранного и что **проверки подлинности** имеет значение **Без проверки подлинности**.

3. Назовите проект **MyASPApp** и нажмите кнопку **ОК** для создания нового решения.

4. Откройте файл About.cshtml.cs и установите точку останова в `OnGet` метода (в старые шаблоны откройте HomeController.cs вместо и задать точку останова в `About()` метода).

## <a name="remote_debug_azure_app_service"></a> Удаленная отладка ASP.NET Core в службе приложений Azure

Из Visual Studio можно быстро публиковать и отладка приложения, чтобы полностью подготовленные экземпляр IIS. Однако предустановку конфигурации IIS и его нельзя настроить. Более подробные инструкции см. в разделе [развернуть веб-приложение ASP.NET Core в Azure, с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Если требуется возможность настройки IIS, попробуйте отладить [виртуальной Машины Azure](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Чтобы развернуть приложение и удаленной отладки с помощью обозревателя серверов

1. В Visual Studio, щелкните правой кнопкой мыши узел проекта и выберите команду **публикации**.

    Если были настроены ранее все профили публикации **публикации** появится область. Нажмите кнопку **новый профиль**.

1. Выберите **службе приложений Azure** из **публикации** выберите **создать новый**и следуйте инструкциям на экране для публикации.

    Подробные инструкции см. в разделе [развернуть веб-приложение ASP.NET Core в Azure, с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Публикация в службу приложений Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Откройте **обозревателя серверов** (**представление** > **обозревателя серверов**), щелкните правой кнопкой мыши в экземпляре приложения и выберите **присоединить отладчик**.

1. В работающем приложении ASP.NET, щелкните ссылку, чтобы **о** страницы.

    В Visual Studio должна быть достигнута точка останова.

    Вот и все! Остальные шаги в этом разделе применяются к удаленную отладку на Виртуальной машине Azure.

## <a name="remote_debug_azure_vm"></a> Удаленная отладка ASP.NET Core на Виртуальной машине Azure

Можно создать Azure VM для Windows Server и затем установить и настройки служб IIS и другие необходимые программные компоненты. Это занимает больше времени, чем развертывание для службы приложения Azure и требует выполните оставшиеся действия в этом учебнике.

Во-первых, выполните действия, описанные в [установки и запуска IIS](/azure/virtual-machines/windows/quick-create-portal).

Если открыть порт 80 в группу безопасности сети, также можно откройте порт 4022 удаленного отладчика. В этом случае не придется открыть его позже.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Приложение уже выполняется в службах IIS на виртуальной Машине Azure?

Эта статья содержит инструкции по настройке основную конфигурацию служб IIS в Windows server и развертывания приложения из Visual Studio. Чтобы убедиться в том, что на сервере установлены необходимые компоненты установлены, приложение может выполняться правильно и что вы готовы к удаленной отладки включены следующие действия.

* Если приложение запущено в службах IIS и просто хотите загрузить удаленного отладчика и начать отладку, перейдите на [Загрузите и установите инструменты удаленной отладки на Windows Server](#BKMK_msvsmon).

* Если требуется помощь, чтобы убедиться в том, что приложения настроены, развернуты и правильно на сервере IIS, чтобы выполнить отладку, выполните все действия в этом разделе.

### <a name="update-browser-security-settings-on-windows-server"></a>Обновить параметры безопасности браузера в Windows Server

Если конфигурация усиленной безопасности включена в Internet Explorer (включено по умолчанию), может потребоваться добавить некоторые домены как доверенных узлов, чтобы можно было загрузить некоторые компоненты веб-сервера. Добавить надежные сайты, перейдите к **свойства обозревателя > Безопасность > надежных узлов > сайтов**. Добавьте следующие домены.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

При загрузке программного обеспечения, можно получить запросы на предоставление разрешения на загрузку различные сценарии веб-сайт и ресурсы. Некоторые из этих ресурсов не являются обязательными, но чтобы упростить процесс, нажмите кнопку **добавить** при появлении запроса.

### <a name="install-aspnet-core-on-windows-server"></a>Установка ASP.NET Core в Windows Server

1. Установка [.NET Core Windows Server, где размещены](https://aka.ms/dotnetcore-2-windowshosting) пакета на хост-системы. Пакет для установки среды выполнения .NET Core, основной библиотеке .NET и модуль ASP.NET Core. Более подробные инструкции см. в разделе [публикация в службах IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Если система не использует подключение к Интернету, загрузка и установка *[Visual C++ 2015 распространяемый компонент Microsoft](https://www.microsoft.com/download/details.aspx?id=53840)* перед установкой пакета .NET Core Windows Server, где размещены.

3. Перезагрузку системы (или выполните **net stop был /y** следуют **net start w3svc** из командной строки, чтобы отобразить изменение в системе путь).

## <a name="choose-a-deployment-option"></a>Выберите вариант развертывания

Если необходимо выполнить развертывание приложения в IIS, рассмотрим следующие варианты.

* Разверните, создав файл параметров публикации в службах IIS и импорта параметров в Visual Studio. В некоторых сценариях это быстрый способ развертывания приложения. При создании файла параметров публикации разрешения автоматически настраиваются в службах IIS.

* Развертывание путем публикации в локальную папку и копирование выходных данных предпочтительным методом в папку подготовленного приложения в IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Необязательно) Развертывание с помощью файла параметров публикации

Этот параметр можно использовать создать файл параметров публикации и импортировать его в Visual Studio.

> [!NOTE]
> Этот метод развертывания использует веб-развертывания. Если вы хотите настроить веб-развертывания вручную в Visual Studio вместо импорта параметров, можно установить 3.6 Развертывание Web вместо 3.6 Развертывание Web для размещения серверов. Тем не менее, при настройке веб-развертывания вручную, необходимо убедиться, что папка приложений на сервере настроены правильные значения и разрешения (см. [Настройка веб-узла ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Установка и настройка веб-развертывания для размещения серверов в Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Создать файл параметров публикации в службах IIS в Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Импорт параметров публикации в Visual Studio и развертывание

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

После успешного развертывает приложение, должен запускаться автоматически. Если приложение не запускается из Visual Studio, запустите приложение в службах IIS. Для ASP.NET Core необходимо убедитесь в том, что пул приложений поля для **DefaultAppPool** равно **без управляемого кода**.

1. В **параметры** диалоговое окно, включите отладку, последовательно щелкнув **Далее**, выберите **отладки** конфигурации, а затем выберите **удалить дополнительные файлы в Назначение** под **опубликовать файл** параметры.

    > [!NOTE]
    > При выборе конфигурации выпуска отключить отладку в *web.config* файлов при публикации.

1. Нажмите кнопку **Сохранить** и повторно опубликуйте приложение.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Необязательно) Публикуя их в локальной папке развертывания

Этот параметр можно использовать для развертывания приложения, если вы хотите скопировать приложение в IIS с помощью Powershell, RoboCopy, или необходимо вручную скопировать файлы.

### <a name="BKMK_deploy_asp_net"></a> Настройка веб-узла ASP.NET на сервере Windows Server

При импорте параметров публикации, данный раздел можно пропустить.

1. Откройте **Диспетчер служб IIS** и перейдите к разделу **Сайты**.

2. Щелкните правой кнопкой мыши узел **Веб-сайт по умолчанию** и выберите команду **Добавить приложение**.

3. Задать **псевдоним** на **MyASPApp** и поле пула приложения **без управляемого кода**. Задать **физический путь** для **C:\Publish** (где будут развернуты позднее проекта ASP.NET).

4. С сайта, выбранного в диспетчере служб IIS, выберите **изменение разрешений**и убедитесь, что учетная запись IUSR, IIS_IUSRS или пользователь, настроен для пула приложений имеет полномочному пользователю с правами на чтение и выполнение.

    Если вы не видите одному из этих пользователей с доступом, выполните действия, чтобы добавить IUSR в качестве пользователя с правами на чтение и выполнение.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Необязательно) Публикация и развертывание приложения путем публикации в локальную папку из Visual Studio

Если вы не используете веб-развертывания, необходимо опубликовать и развертывание приложения с помощью файловой системы или других средств. Можно начать с создания пакета в файловой системе и затем развернуть пакет вручную или использовать другие средства, такие как PowerShell, XCopy или RoboCopy. В этом разделе предполагается, что пакет выполняется копирование вручную в случае, если вы не используете веб-развертывания.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Загрузите и установите инструменты удаленной отладки на Windows Server

В этом учебнике мы используем Visual Studio 2017 г.

Если не удается открыть страницу при загрузке удаленного отладчика, см. раздел [разблокировать Загрузка файла](../debugger/remote-debugging.md#unblock_msvsmon) для справки.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Настройка удаленного отладчика на Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Если необходимо добавить разрешения для других пользователей, изменение режима проверки подлинности, или номер порта удаленного отладчика, в разделе [настроить удаленный отладчик](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Подключение к приложению ASP.NET с компьютера с Visual Studio

1. На компьютере с Visual Studio откройте решение, которое вы пытаетесь отладить (**MyASPApp** Если вы следуете инструкциям в этой статье).
2. В Visual Studio щелкните **Отладка > присоединить к процессу** (Ctrl + Alt + P).

    > [!TIP]
    > В Visual Studio 2017 г., вы можете повторно присоединить с тем же процессом, ранее присоединена к с помощью **Отладка > повторно присоединиться к процессу...** (Shift + Alt + P). 

3. Задайте для поля квалификатор  **\<имя удаленного компьютера >: 4022**.
4. Нажмите кнопку **Обновить**.
    В окне **Доступные процессы** должен появиться ряд процессов.

    Если вы не видите все процессы, попробуйте использовать IP-адрес вместо имени удаленного компьютера (порт является обязательным). Можно использовать `ipconfig` в командной строке, чтобы получить адрес IPv4.

    Если вы хотите использовать **найти** кнопки, может потребоваться [откройте порт UDP 3702](#bkmk_openports) на сервере.

5. Установите флажок  **Показать процессы, запущенные всеми пользователями**.

6. Введите имя процесса, чтобы быстро найти первую букву *dotnet.exe* (для ASP.NET Core).
   
   Для приложения ASP.NET Core, было имя предыдущего процесса *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Нажмите кнопку **Присоединить**.

8. Откройте веб-сайт удаленного компьютера. В браузере, перейдите к **http://\<имя удаленного компьютера >**.
    
    Должна открыться веб-страница ASP.NET.
9. В работающем приложении ASP.NET, щелкните ссылку, чтобы **о** страницы.

    В Visual Studio должна быть достигнута точка останова.

### <a name="bkmk_openports"></a> Устранение неполадок: Откройте требуемых портов в Windows Server

В большинстве установок необходимые порты открыты путем установки ASP.NET и удаленный отладчик. Тем не менее если приложение будет размещено за брандмауэром Устранение неполадок развертывания, может потребоваться убедитесь, что необходимые порты открыты.

На виртуальной Машине Azure, необходимо открыть порты, через [сетевой группы безопасности](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Необходимые порты:

- 80 - требуется для служб IIS
- 4022 - необходимых для удаленной отладки из Visual Studio 2017 г. (см. [назначение портов удаленного отладчика](../debugger/remote-debugger-port-assignments.md) для получения дополнительной информации).
- UDP 3702 - порта (необязательно) обнаружения позволяет **найти** кнопку при присоединении удаленного отладчика в Visual Studio.

Кроме того эти порты уже открывать путем установки ASP.NET:
- 8172 - (требуется необязательно) для веб-развертывания для развертывания приложения из Visual Studio

