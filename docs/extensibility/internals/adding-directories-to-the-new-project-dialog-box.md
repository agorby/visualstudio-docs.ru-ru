---
title: Добавление каталогов в диалоговое окно создания проекта | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4ad992785fdf8ab5ffdd3faa7043e2a0ee5411b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Добавление каталогов в диалоговое окно нового проекта
При создании новых типов проектов, также можно зарегистрировать новый каталог в **новый проект** диалогового окна их для использования в качестве шаблонов. В следующем примере кода описывается регистрация нового каталога, также известные как узел. В примере шаблоны, предоставляемые VSPackage CLSID_Package регистрируются. Таким образом, в левой части **новый проект** диалоговое окно предоставляет добавленный узел с именем определяется Folder_Label_ResID ресурсов. Этот ресурс загружается из DLL-Библиотеке дополнения VSPackage.  
  
 **Папки** значение представляет идентификатор GUID папки, в которой отображается узел Folder_Label_ResID. В примере представляет идентификатор GUID **другие проекты** папки в **типы проектов** области **новый проект** диалоговое окно. Если **другие проекты** значение отсутствует, то она позиционируется на верхнем уровне.  
  
 Значение TemplatesDir указывает полный путь каталога, который содержит шаблоны проектов. Эти файлы могут быть VSZ-файлы или файлы типичный шаблон для клонирования.  
  
 При указании TemplatesLocalizedSubDir он должен быть Идентификатором ресурса из строки с именем подкаталога TemplatesDir, который содержит локализованные шаблоны. Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает строкового ресурса из вспомогательной библиотеки DLL, если она есть, каждой вспомогательной библиотеки DLL может содержать различные подкаталог с именем. Значение SortPriority указывает приоритет сортировки.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Добавление новых элементов"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)