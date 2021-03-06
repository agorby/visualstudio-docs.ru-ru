---
title: Начало работы с C# и ASP.NET Core в Visual Studio
ms.custom: ''
ms.date: 12/11/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 3de8a60b6f9f4807bd0032fc457a9040f937c063
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765519"
---
# <a name="get-started-with-c-and-aspnet-in-visual-studio"></a>Начало работы с C# и ASP.NET в Visual Studio

В этом учебнике по разработке на языке C# с помощью ASP.NET Core в Visual Studio вы создадите веб-приложение ASP.NET Core на C#, добавите в него код, изучите некоторые возможности интегрированной среды разработки и запустите приложение.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

## <a name="before-you-begin"></a>Подготовка к работе

Ниже приведен краткий список вопросов и ответов, с помощью которого вы сможете ознакомиться с некоторыми основными понятиями.

### <a name="what-is-c"></a>Что такое C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) — это типобезопасный объектно-ориентированный язык программирования, который обладает широкими возможностями, но в то же время прост в обучении.

### <a name="what-is-aspnet-core"></a>Что такое ASP.NET Core?

ASP.NET Core — это кроссплатформенная платформа с открытым кодом для создания приложений, подключенных к Интернету, таких как веб-приложения и службы. Приложения ASP.NET Core могут работать на основе .NET Core или .NET Framework. Приложения ASP.NET Core можно разрабатывать и запускать на различных платформах, включая Windows, Mac и Linux. Код ASP.NET Core открыт для общего доступа в [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Что такое Visual Studio?

Visual Studio — это интегрированный набор средств разработки. Его можно рассматривать как программу для создания приложений.  

## <a name="start-developing"></a>Начало разработки

Готовы приступить к разработке? Вперед!

### <a name="create-a-project"></a>Создание проекта

Сначала создадим проект ASP.NET Core. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual C#**, затем разверните узел **Веб** и выберите **.NET Core**. В средней области выберите **Веб-приложение ASP.NET Core**, присвойте файлу имя *MyCoreApp* и нажмите кнопку **ОК**.

   ![Шаблон проекта "Веб-приложение ASP.NET Core" в диалоговом окне "Новый проект" в интегрированной среде разработки Visual Studio](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Добавление рабочей нагрузки (необязательно)

Если шаблон проекта **Веб-приложение ASP.NET Core** отсутствует, его можно получить, добавив рабочую нагрузку **ASP.NET и разработка веб-приложений**. Добавить ее можно одним из двух способов в зависимости от того, какие обновления Visual Studio 2017 установлены на вашем компьютере.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Способ 1. Диалоговое окно "Новый проект"

1. Щелкните ссылку **Открыть установщик Visual Studio** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Способ 2. Меню "Сервис"

1. Закройте диалоговое окно **Новый проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**.

2. Запускается Visual Studio Installer. Выберите рабочую нагрузку **ASP.NET и разработка веб-приложений**, а затем щелкните **Изменить**.

#### <a name="add-a-project-template"></a>Добавление шаблона проекта

1. В диалоговом окне **Создать веб-приложение ASP.NET Core** выберите шаблон проекта **Веб-приложение (Model-View-Controller)**.  

2. В раскрывающемся меню выберите пункт **ASP.NET Core 2.0**. (Если вы не видите **ASP.NET Core 2.0** в списке, установите его, пройдя по ссылке на **скачивание**, которая должна появиться в желтой строке в верхней части диалогового окна.) Нажмите кнопку **ОК**.

   ![Диалоговое окно "Создать веб-приложение ASP.NET Core"](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Сведения о решении

Это решение строится на основе модели архитектуры MVC, которая разделяет приложение на три основных компонента:

* **Модели** включают в себя классы, представляющие данные приложения. Классы модели используют логику проверки, которая позволяет применять бизнес-правила к этим данным. Как правило, объекты модели извлекают и сохраняют состояние модели в базе данных.
* **Представления** — это компоненты, которые формируют пользовательский интерфейс приложения. Как правило, в пользовательском интерфейсе отображаются данные модели.
* **Контроллеры** включают в себя классы, которые обрабатывают запросы браузера. Они извлекают данные модели и вызывают шаблоны представлений, которые возвращают ответ. В приложении MVC представление служит только для отображения информации. Обработку вводимых данных, реагирование и взаимодействие с пользователем обеспечивает контроллер.

С помощью модели MVC можно создавать приложения, которые тестировать и обновлять удобнее, чем традиционные монолитные приложения.

### <a name="tour-your-solution"></a>Обзор решения

 1. С помощью шаблона проекта создается решение с одним проектом ASP.NET Core, который имеет имя **MyCoreApp**. Разверните узел проекта, чтобы увидеть его содержимое.

    ![Обозреватель решений ASP.NET в Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

 2. Откройте файл *HomeController.cs* в папке **Controllers**.

     ![Файл HomeController.cs в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 3. Просмотрите содержимое файла *HomeController.cs*.

     ![Файл HomeController.cs в окне кода Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 4. Кроме того, проект включает в себя папку **Views**, которая содержит другие папки, соответствующие каждому контроллеру (а также папку для **общих** представлений). Например, файл CSHTML (расширение HTML) представления для пути */Home/About* будет находиться по пути *Views/Home/About.cshtml*. Откройте этот файл.

     ![Файл About.cshtml в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

 5. Этот файл CSHTML использует синтаксис Razor для отрисовки HTML на основе сочетания стандартных тегов и встроенного кода C#.

     ![Файл About.cshtml в окне кода Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

   >[!NOTE]
   > Дополнительные сведения см. на странице [Начало работы с C# и ASP.NET с использованием синтаксиса Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

 6. Решение также содержит папку *wwwroot*, которая является корнем веб-сайта. Вы можете поместить статическое содержимое сайта, такое как CSS, изображения и библиотеки JavaScript, непосредственно по путям, по которым оно должно находиться при развертывании сайта.

     ![Папка wwwroot в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

 7. Имеются также различные файлы конфигурации, которые служат для управления проектом, его пакетами и приложением во время выполнения. Например, [конфигурация](/aspnet/core/fundamentals/configuration) приложения по умолчанию хранится в файле *appsettings.json*. Однако можно переопределять некоторые или все эти параметры для той или иной среды, например, предоставив файл *appsettings.Development.json* для среды **разработки**.

     ![Файлы конфигурации в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Запуск и отладка приложения

1. Чтобы выполнить сборку приложения и запустить его в режиме отладки, нажмите в интегрированной среде разработки кнопку **IIS Express**. (Кроме того, можно нажать клавишу **F5** или выбрать пункт меню **Отладка > Начать отладку**.)

   ![Нажмите кнопку "IIS Express" в Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Если появляется сообщение об ошибке **Не удается подключиться к веб-серверу "IIS Express"**, закройте среду Visual Studio и откройте ее с помощью пункта **Запуск от имени администратора** в контекстном меню. Затем снова запустите приложение.

2. Visual Studio откроет окно браузера. Выберите вкладку **About** (Сведения).

   ![Выбор вкладки "About" в окне браузера с приложением](../ide/media/csharp-aspnet-browser-page.png)

 Помимо прочего, на странице **About** в браузере отображается текст, заданный в файле *HomeController.cs*.

   ![Просмотр текста на странице "About"](../ide/media/csharp-aspnet-browser-page-about.png)

3. Не закрывая окно браузера, вернитесь в Visual Studio. Откройте файл *Controllers/HomeController.cs*, если он еще не открыт.

   ![Открытие файла HomeController.cs в обозревателе решений Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

4. Установите точку останова в первой строке метода **About**. Для этого щелкните в поле или установите курсор в этой строке и нажмите клавишу **F9**.

  В этой строке задаются данные в коллекции **ViewData**, которые отображаются на CSHTML-странице по пути *Views/Home/About.cshtml*.

   ![Установите точку останова в первой строке метода About в файле About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

5. Вернитесь в браузер и обновите страницу **About**. В Visual Studio будет достигнута точка останова.

6. В Visual Studio наведите указатель на член **ViewData**, чтобы просмотреть его данные.

   ![Просмотр дополнительных сведений о члене ViewData метода About](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

7. Удалите точку останова в приложении, выполнив те же действия, что и для ее добавления.

8. Откройте файл *Views/Home/About.cshtml*.

   ![Выбор файла About.cshtml в обозревателе решений](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

9. Замените слово **additional** на **changed** и сохраните файл.

   ![Замена слова "additional" на "changed"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

10. Вернитесь в окно браузера, чтобы увидеть новый текст. (Если вы не видите измененный текст, обновите содержимое окна.)

    ![Обновление содержимого окна браузера для отображения измененного текста](../ide/media/csharp-aspnet-browser-page-about-changed.png)

11. Чтобы остановить отладку, на панели инструментов нажмите кнопку **Остановить отладку**. (Кроме того, можно нажать клавишу **SHIFT**+**F5** или выбрать пункт меню **Отладка** > **Остановить отладку**.)

   ![Нажатие кнопки "Остановить отладку" на панели инструментов](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>Следующие шаги

Поздравляем с завершением этого учебника! Надеемся, что вы узнали что-то новое о C#, ASP.NET Core и интегрированной среде разработки Visual Studio. Для получения дополнительных сведений перейдите к следующему учебнику.

 > [!div class="nextstepaction"]
 > [Начало работы с MVC ASP.NET Core и Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)
