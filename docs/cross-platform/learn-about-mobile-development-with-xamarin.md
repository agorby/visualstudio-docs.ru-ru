---
title: Подробности о разработке мобильных приложений с использованием Xamarin | Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.prod: xamarin
ms.technology: xamarin-tools
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 921faa49690b641fda0e864d27705040a1b97f1e
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Подробности о разработке мобильных приложений с использованием Xamarin

В этой статье перечислено несколько обзоров, которые помогут вам понять процесс разработки кроссплатформенных мобильных приложений с помощью Xamarin. Если вы еще не установили Visual Studio и Xamarin, сначала запустите процесс [Настройка и установка](../cross-platform/setup-and-install.md) , затем вернитесь сюда, чтобы изучить представленные ниже материалы во время выполнения программы установки.  
  
> [!NOTE]
> Если не указано иное, можно сначала читать указанные непосредственно здесь страницы и не переходить по ссылкам на их дочерние страницы. Если после освоения этого списка процесс установки по-прежнему выполняется, вы можете вернуться и изучить дополнительные разделы.  
>   
> Также вы можете просмотреть статьи "Основы" и вернуться к статьям "Подробное рассмотрение" позже.  
  
## <a name="essentials-introduction-to-xamarin"></a>Основы: введение в Xamarin  

*10–20 минут*  
  
1.  [Мобильные приложения в Visual Studio с Xamarin](https://www.visualstudio.com/xamarin/) (visualstudio.com) предоставляют краткое сводное описание основных характеристик Xamarin.  
  
2.  [Создание кроссплатформенных мобильных приложений с помощью C# и Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15 мин. 16 сек.) с пропагандистом Xamarin, Джеймсом Монтеманьо (James Montemagno). Первые три минуты посвящены обзору Xamarin, затем следуют демонстрации кода.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Основы: обзор окружений Visual Studio и Xamarin  

*5–15 минут*  
  
-   Основная часть работы выполняется на компьютерах Windows с установленными Visual Studio и Xamarin. На таких компьютерах напрямую создаются приложения для Windows и Android, а также выполняются их запуск и отладка на рабочем столе, устройстве или эмуляторе. Вы также можете удаленно создавать, запускать и отлаживать приложения iOS на компьютере Mac. В Visual Studio на компьютере Windows можно также подключиться к конструктору раскадровки iOS и симулятору iOS.  
  
-   Компьютер Mac с установленными Xcode и Visual Studio для Mac служит узлом сборки, узлом подписывания и средой выполнения для приложений iOS. Компьютер с Windows делегирует сборку для iOS компьютеру Mac. Приложение запускается в симуляторе iOS на компьютере Mac или непосредственно на связанном устройстве, подключенном к Mac. Можно взаимодействовать с приложением на компьютере Mac, а отладку проводить в Visual Studio.
  
Схема процесса изображена ниже.  
  
![Связь между компьютерами для разработки ПО Windows и Mac в среде Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "Изучение CrossPlat Xamarin 1")  

> [!NOTE]
> Windows Phone изображен на схеме для обеспечения полноты информации. При использовании платформы Xamarin рекомендуемым вариантом совместного применения кода является использование библиотеки .NET Standard 2.0, которая несовместима с устройствами Windows Phone и Windows 10 Mobile. 

Дополнительные сведения о работе с приложениями iOS см. в статье [Введение в Xamarin.iOS для Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/).
  
## <a name="essentials-how-projects-are-structured"></a>Основы: как структурированы проекты  

*10–30 минут*  
  
1.  [Варианты совместного использования кода](/xamarin/cross-platform/app-fundamentals/code-sharing/). В новых приложениях для совместного использования кода следует использовать библиотеку .NET Standard. Большая часть кода бизнес-логики будет находиться в библиотеке NET Standard, включая доступ к базам данных, вызовы интерфейсов API REST и вызовы портативных компонентов Xamarin. (См. раздел [Deeper Dive: Xamarin Components](#components) в конце этой статьи.) Общий код пользовательского интерфейса, написанный с помощью Xamarin.Forms, также находится в библиотеке NET Standard.  
  
2.  В статье [Практический пример: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) описаны рекомендации по разработке и структурированию полнофункционального приложения, например структурирование проекта с общим кодом, который разделяет данные, доступ к данным и бизнес-уровни (необязательно).  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Основы: встроенные слои и слои пользовательского интерфейса Xamarin.Forms  

*10–40 минут*  
  
Xamarin предоставляет два способа для создания отличных приложений: Xamarin Native и Xamarin.Forms.  
  
В Xamarin Native можно написать отдельный код пользовательского интерфейса для каждой целевой платформы: iOS, Android и Windows.  Такой подход дает прямой доступ к интерфейсам API платформы, позволяя разрабатывать пользовательский интерфейс для каждой платформы.  Также имеется полный доступ к нативному конструктору и элементам управления для каждой платформы, чтобы помочь в создании соответствующего пользовательского интерфейса.  
  
Xamarin.Forms предоставляет общий набор интерфейсов API, который позволяет создавать общий уровень пользовательского интерфейса для всех платформ в библиотеке .NET Standard.  Xamarin.Forms отрисовывает нативные элементы управления для каждой целевой платформы, чтобы обеспечить знакомый внешний вид и ощущения.  Вместо использования конструктора можно создать свой пользовательский интерфейс с помощью C# и XAML.  

Большинство разработчиков использует Xamarin.Forms. Это рекомендуемый путь для начинающих разработчиков Xamarin. Подход Xamarin Native является более сложным и требует глубоких знаний о целевых платформах.
  
Не нужно решать, какой подход использовать сразу, — приложения могут быть реализованы с помощью сочетания Xamarin Native и Xamarin.Forms.  
  
-   Используйте Xamarin.Forms для создания экранов общего назначения. Это позволит создать сходный пользовательский интерфейс и возможности на разных платформах, например страницы для входа, формы контактов и результаты поиска.  
  
-   Используйте различные возможности в Xamarin.Forms для настройки пользовательского интерфейса отдельно для каждой платформы. Самый простой вариант настройки включает в себя API `OnPlatform`. Можно также создавать пользовательские представления, расширять возможности встроенных отрисовщиков и создавать свои собственные.  
  
-   При необходимости используйте Xamarin Native для создания экранов, использующих уникальные функции пользовательского интерфейса на каждой платформе. Например, можно создать экран, который использует собственный механизм захвата с камеры и обработку изображений.  
  
Обычно следует начинать с решения на Xamarin.Forms, чтобы настроить совместное использование кода, создающего пользовательский интерфейс, на нескольких платформах. Затем используйте возможности тонкой настройки для корректировки под конкретную платформу. Если и когда требуется создавать экраны полностью под определенную платформу, можно добавить их по отдельности с помощью Xamarin Native.  
  
Дополнительные сведения:  
  
1.  [Xamarin.Forms](/xamarin/xamarin-forms/) предоставляет краткий обзор, а также сравнение Xamarin.Forms и уровней нативного пользовательского интерфейса (то есть Xamarin.iOS и Xamarin.Android).  
  
2.  Первые три минуты видео Джеймса Монтеманьо [Xamarin.Forms: создание нативных приложений iOS, Android и Windows с помощью C# и XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13 мин 3 с) содержат еще один обзор; остальная часть видео посвящена демонстрациям.  
  
3.  [Введение в Xamarin.Forms](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/) (необязательно).  
  
4.  Примеры использования `OnPlatform` для настройки см. в документации по [классу Device](/xamarin/xamarin-forms/platform/device/) (необязательно).
  
5.  Статья [Кроссплатформенная разработка — общий доступ к коду пользовательского интерфейса на мобильных платформах с помощью Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx), автор Джейсон Смит (Jason Smith) из MSDN Magazine. В статье описаны разные возможности настройки в Xamarin.Forms, подробнее о которых написано в другой статье [Пользовательские отрисовщики](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (необязательно).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Подробное рассмотрение: отладка с помощью эмуляторов  

*10–15 минут*  
  
Для отладки кроссплатформенных приложений без использования физического устройства необходимо использовать эмуляторы, работа с которыми описывается в следующих статьях:  
  
### <a name="microsofts-android-emulator"></a>Эмулятор Android Microsoft 

Рекомендуется использовать [Эмулятор Visual Studio для Android](visual-studio-emulator-for-android.md) компании Майкрософт, который устанавливается вместе с Visual Studio.  Видео об [эмуляторе Visual Studio для Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Channel9, 5 мин. 55 сек.) содержит еще один обзор и демонстрацию.  
  
### <a name="apples-ios-simulator"></a>Симулятор iOS Apple

Дополнительные сведения см. в статье [Начало работы с симулятором iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
### <a name="microsofts-windows-phone-emulator"></a>Эмулятор Microsoft Windows Phone.

Дополнительные сведения см. в статье [Тестирование с помощью эмулятора устройства с Windows 10 Mobile (Майкрософт)](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/).  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>Deeper Dive: Xamarin Components  

*10 минут*  
  
Многие расширенные возможности доступны для приложений Xamarin через компоненты Xamarin. Полный каталог доступен для скачивания на сайте [http://components.xamarin.com/](http://components.xamarin.com/) и включает в себя компоненты для дополнительных элементов управления пользовательского интерфейса, проверки подлинности, разнообразные облачные службы, например Microsoft Azure, и многое другое.