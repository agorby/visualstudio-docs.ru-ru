---
title: 'Как: получение данных для встроенного узла SharePoint в обозревателе серверов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f448ec8d7cfe22495aa3f7b2ce9191f106205c33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Практическое руководство. Получение данных для встроенного узла SharePoint в обозревателе сервера
  Для каждого узла SharePoint, встроенного в **обозревателя серверов**, можно получить данные по указанному компоненту SharePoint, которую представляет узел. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано получение данных по указанному списку SharePoint, который представлен в узле списка в **обозревателя серверов**. По умолчанию узлы списка содержат **Просмотр в браузере** пункт контекстного меню, которую можно щелкнуть, чтобы открыть список в веб-браузере. В этом примере расширяет список узлов, добавляя **представление в Visual Studio** пункт контекстного меню, который позволяет открыть списки непосредственно в Visual Studio. Код обращается к данным списка для узла, чтобы получить URL-адрес из списка, чтобы открыть в Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 В этом примере используется служба проекта SharePoint для получения <xref:EnvDTE.DTE> объект, используемый для открытия списков в Visual Studio. Дополнительные сведения о службе проекта SharePoint см. в разделе [использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Дополнительные сведения об основных задачах для создания расширения узла SharePoint см. в разделе [как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Развертывание расширения  
 Для развертывания **обозревателя серверов** расширения, создать [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и другие файлы, которые требуется распространить с расширением. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  