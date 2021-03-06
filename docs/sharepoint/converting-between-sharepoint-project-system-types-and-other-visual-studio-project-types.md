---
title: Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64de38fe796ce3c1e0d333a22582ad2973e1c4d2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765363"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio
  В некоторых случаях может потребоваться объект в системе проекта SharePoint, и вы хотите использовать возможности соответствующего объекта в объектной модели автоматизации Visual Studio или объектной модели интеграции и наоборот. В этих случаях можно использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> метода службы проектов SharePoint для преобразования объекта в другой объектной модели.  
  
 Например, может потребоваться <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объект, но вы хотите использовать методы, которые доступны только для <xref:EnvDTE.Project> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> объекта. В этом случае можно использовать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> метод преобразования <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> для <xref:EnvDTE.Project> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Дополнительные сведения об объектной модели автоматизации Visual Studio и объектная модель интеграции Visual Studio см. в разделе [Общие сведения о программировании модели из расширения инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Типы преобразований
 Ниже перечислены типы, которые можно преобразовать этот метод между системы проектов SharePoint и другие модели объектов Visual Studio.  
  
|Тип системы проектов SharePoint|Соответствующие типы в объектных моделях автоматизации и интеграции|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> или<br /><br /> Любой интерфейс в объектной модели интеграции Visual Studio, реализуемый базовым COM-объектом проекта. Среди этих интерфейсов: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (или производный интерфейс) и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Список главных интерфейсов, реализуемых в проектах см. в разделе [основные компоненты модели проекта](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> или<br /><br /> Объект<xref:System.UInt32> (также называемые VSITEMID) значение, которое определяет элемент проекта в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , которая его содержит. Это значение может быть передан *itemid* параметр некоторых <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> методы.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется использование <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> метод преобразования <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> объект <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 Для этого примера требуются:  
  
-   Расширение системы проектов SharePoint, который содержит ссылку на *EnvDTE.dll* сборки. Дополнительные сведения см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Код, который регистрирует `projectService_ProjectAdded` метод для обработки <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> событие <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объекта. Пример см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>См. также
 [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Как: извлечение службы проектов SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Обзор модели программирования для расширений средств SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
