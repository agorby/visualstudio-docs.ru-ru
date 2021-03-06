---
title: 'Как: программное удаление листов из книг | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d6e9095890212debb8ab845ac7411c734b9a427
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Практическое руководство. Программное удаление листов из книг
  В книге можно удалить любой лист. Для удаления листа используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>Использование ведущего элемента листа  
 Если лист был добавлен в настройку на уровне документа во время разработки, для удаления указанного листа используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Следующий код удаляет лист из книги с помощью прямой ссылки на ведущий элемент листа.  
  
> [!IMPORTANT]  
>  Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:  
>   
>  -   Книга Excel 2013  
> -   Шаблон Excel 2013  
> -   Книга Excel 2010  
> -   Шаблон Excel 2010  
>   
>  Если вы хотите выполнить эту задачу в проекте любого другого типа, необходимо добавить ссылку на **Microsoft.Office.Interop.Excel** сборки, а затем использовать классы из этой сборки, чтобы открыть книгу и удалить лист. Дополнительные сведения см. в разделе [как: целевой Office приложениям через основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Excel 2010 основной сборке взаимодействия](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Удаление листа с помощью ведущего элемента листа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> типа `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel  
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.  
  
-   Требуется удалить лист в надстройке VSTO.  
  
-   Лист, который требуется удалить, был создан во время выполнения в настройке на уровне документа.  
  
 Следующий код удаляет лист из книги с помощью ссылки на лист при использовании номера индекса **листов** коллекции. В этом коде предполагается, что новый лист был создан программным образом.  
  
> [!IMPORTANT]  
>  Если вы хотите выполнить эту задачу в проекте любого другого типа, необходимо добавить ссылку на **Microsoft.Office.Interop.Excel** сборки, а затем использовать классы из этой сборки, чтобы открыть книгу и удалить лист. Дополнительные сведения см. в разделе [как: целевой Office приложениям через основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Excel 2010 основной сборке взаимодействия](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Удаление листа с помощью коллекции листов книги Excel  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Как: программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Как: программный Выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)   
 [Как: программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  