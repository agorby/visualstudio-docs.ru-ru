---
title: Отладка с помощью предварительно загруженными содержимое в приложениях UWP | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 241937c8462577d6af375d2440efe828a738a8cc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Отладка приложения UWP, с помощью предварительно загруженными содержимое в Visual Studio
  
 Для ускорения ответа приложения UWP, можно создать запрос Windows на предварительную загрузку определенного веб-содержимого, например веб-страниц или изображений, в приложении [WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c) кэша. Эта функциональность называется предварительной загрузкой. Это особенно эффективен для содержимого, которое используется при запуске, но также можно выполнять предварительную загрузку другого часто используемого содержимого слишком. Методы [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) позволяют указывать URI содержимого, которое необходимо предварительно загрузить. См. в Windows SDK [пример предварительной загрузки содержимого](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) примеры добавления функциональности ContentPrefetcher в приложение.  
  
 Windows использует эвристику для определения времени и необходимости выполнения предварительной загрузки, а также того, какие ресурсы будут загружены. Эта эвристика учитывает условия питания и системной сети, историю использования приложения пользователем, а также результаты предыдущих попыток предварительной загрузки. В Visual Studio можно использовать **запустить предварительную загрузку приложения магазина Windows** команду, чтобы принудить Windows к игнорированию эвристики ContentPrefetcher и выполнению предварительной загрузки всего указанного веб-содержимого. Это может быть полезно, если требуется протестировать поведение или производительность приложения с содержимым, которое необходимо предварительно загрузить в известном состоянии (либо загруженном, либо незагруженном).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Принудительная предварительная загрузка ресурсов, указанных ContentPrefetcher  
 В этой процедуре предполагается, что вы уже настроили функцию ContentPrefetcher и указали URI содержимого, которое необходимо предварительно загрузить в проекте приложения. Для принудительной предварительной загрузки содержимого, если указанные ресурсы являются новыми или изменены, необходимо запустить и остановить приложение перед выбором **запустить предварительную загрузку приложения магазина Windows** команды. Сначала приложение запускается для регистрации URI. **Предварительную загрузку приложения для магазина Windows** команда затем заставляет ContentPrefetcher загрузить содержимое и добавить его в кэш. При дальнейших запусках приложения можно считать, что содержимое предварительно загружается.  
  
1.  Запустите приложение для регистрации URI подлежащего предварительной загрузке содержимого с этим приложением. На **отладки** меню, выберите **начать отладку** (сочетание клавиш: F5).  
  
2.  На **отладки** меню, выберите **остановить отладку** (сочетание клавиш: Shift + F5).  
  
3.  На **отладки** меню, выберите **другие целевые объекты отладки** и выберите **запустить предварительную загрузку приложения магазина Windows**.  
  
 Теперь можно выполнять отладку, тестирование и анализ приложения с предварительно загруженными веб-ресурсами.  
  
> [!NOTE]
>  Повторите эти действия, если необходимо добавить или изменить указанное веб-содержимое.  
  
## <a name="see-also"></a>См. также  
 [Запись блога: запуск предварительной загрузки приложений для магазина Windows в Visual Studio 2013 с обновлением 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)