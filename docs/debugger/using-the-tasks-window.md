---
title: Использование окна задач | Документы Microsoft
ms.custom: ''
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85319575766ca9ff3ace297bf1e4e577d49ee6d9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="using-the-tasks-window"></a>Использование окна задач
**Задачи** напоминает окно **потоков** окна, за исключением того, что он отображает сведения о <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class), или [WinJS.Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) объектов, а не каждый поток. Как и потоки, задачи представляют асинхронные операции, которые могут выполняться параллельно; однако несколько задач могут выполняться в одном потоке. 
  
 В управляемом коде, можно использовать **задачи** окна при работе с <xref:System.Threading.Tasks.Task?displayProperty=fullName> объектов или с **await** и **async** ключевые слова (**Await** и **Async** в VisualBasic). Дополнительные сведения о задачах в управляемом коде см. в разделе [параллельного программирования](/dotnet/standard/parallel-programming/index).  
  
 В машинном коде, можно использовать **задачи** окна при работе с [групп задач](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [параллельные алгоритмы](/cpp/parallel/concrt/parallel-algorithms), [асинхронных агентов](/cpp/parallel/concrt/asynchronous-agents), и [упрощенных задач](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Дополнительные сведения о задачах в машинном коде см. в разделе [среда выполнения с параллелизмом](/cpp/parallel/concrt/concurrency-runtime).  
  
 В JavaScript, можно использовать окна задач при работе с promise `.then` кода. В разделе [асинхронное программирование в JavaScript (приложения UWP)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) для получения дополнительной информации.   
  
 Можно использовать **задачи** окна всякий раз при переключении в режим отладчика. Доступ к нему на **отладки** меню, щелкнув **Windows** и выбрав **задачи**. На следующем рисунке показана **задачи** в режиме по умолчанию.  
  
 ![Окно "задачи"](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  В случае управляемого кода объект <xref:System.Threading.Tasks.Task>, который имеет состояние <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> или <xref:System.Threading.Tasks.TaskStatus>, может не отображаться в окне "Задачи", если управляемые потоки находятся в состоянии сна или состоянии соединения.  
  
## <a name="tasks-column-information"></a>Сведения в столбцах окна "Задачи"  
 Столбцы в **задачи** окна отображаются следующие сведения.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**Флаги**|Показывает, какие задачи помечены, и позволяет помечать задачи и снимать с них метки.|  
|**Значки**|Рядом с текущей задачей отображается желтая стрелка. Текущая задача находится на самом верхнем уровне текущего потока.<br /><br /> Белая стрелка указывает прерванную задачу, т.е. задачу, которая была текущей во время вызова отладчика.<br /><br /> Значок паузы указывает задачу, замороженную пользователем. Задачу можно заморозить или разморозить, щелкнув ее в списке правой кнопкой мыши.|  
|**ID**|Предоставленный системой номер задачи. В машинном коде этот номер является адресом задачи.|  
|**Состояние**|Текущее состояние (запланированные, active, заблокированных, взаимоблокировки, ожидает или завершена) задачи. Запланированная задача – это задача, которая еще не выполнялась и, следовательно, не имеет стека вызова, назначенного потока и других соответствующих сведений.<br /><br /> Активная задача — это задача, которая выполняла код, пока не была прервана в отладчике.<br /><br /> Задача ожидает или заблокированные — один, заблокированная вследствие ожидания сигнала события, освобождения блокировки или завершения другой задачи.<br /><br /> Заблокированная задача – это находящаяся в ожидании задача, чей поток заблокирован другим потоком.<br /><br /> Наведите указатель мыши на **состояние** ячейку задачи заблокированной или ожидает просмотреть дополнительные сведения о блокировке. **Предупреждение:** **задачи** сообщает о состоянии взаимоблокировки только для блокированных задач, использующих примитив синхронизации, который поддерживается по ожидания (Wait Chain Traversal WCT). Например, для заблокированного <xref:System.Threading.Tasks.Task> объекта, использующего WCT, отладчик отображает **взаимоблокировку ожидает**. Для заблокированной задачи, который управляется средой выполнения с параллелизмом, которая не поддерживает WCT, отладчик отображает **ожидания**. Дополнительные сведения о функции WCT см. в разделе [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Время начала**|Время, когда задача стала активной.|  
|**Длительность**|Количество секунд, в течение которого задача была активна.|  
|**Время завершения**|Время, когда задача была завершена.|  
|**Расположение**|Текущее расположение в стеке вызова задачи. Наведите указатель мыши на эту ячейку, чтобы увидеть весь стек вызова задачи. У запланированных задач значение в этом столбце отсутствует.|  
|**Задача**|Исходный метод и какие-либо аргументы, которые были переданы в задачу при ее создании.|  
|**AsyncState**|В случае управляемого кода указывает состояние задачи. По умолчанию этот столбец скрыт. Для отображения этого столбца откройте контекстное меню для одного из заголовков столбцов. Выберите **столбцы**, **AsyncState**.|  
|**Родительский**|Идентификатор задачи, создавшей данную задачу. Если эта ячейка пуста, то у задачи нет родительской задачи. Это применимо только для управляемых программ.|  
|**Назначение потоков**|Идентификатор и имя потока, в котором запущена задача.|  
|**Домен приложения**|Для управляемого кода это домен приложения, в котором выполняется задача.|  
|**task_group**|Для машинного кода, адрес [task_group](/cpp/parallel/concrt/reference/task-group-class.mdd) объекта, который запланировал задачу. Для асинхронных агентов и упрощенных задач этот столбец содержит значение 0.|  
|**Process**|Идентификатор процесса, к которому относится выполняемая задача.|  
  
 В это представление можно добавлять столбцы, щелкнув правой кнопкой мыши заголовок столбца и выбрав нужные столбцы. (Чтобы удалить столбцы, нужно убрать выбор.) Можно также изменять расположение столбцов, перетаскивая их влево или вправо. На следующем рисунке показано контекстное меню столбца.  
  
 ![Контекстное меню представлений в окне задач](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Сортировка задач  
 Чтобы выполнить сортировку задач, щелкните заголовок столбца. Например, щелкнув **идентификатор** заголовок столбца, можно сортировать по ИД задачи: 1,2,3,4,5 и так далее. Чтобы изменить порядок сортировки, еще раз щелкните заголовок столбца. Текущий столбец сортировки и порядок сортировки указывается стрелкой в столбце.  
  
## <a name="grouping-tasks"></a>Группирование задач  
 Задачи можно группировать на основе любого столбца в представлении списка. Например, щелкнув правой кнопкой мыши **состояние** заголовок столбца и выбрав **Group by** > **[*состояние*]**, вы можете сгруппировать все задачи, имеющие одинаковое состояние. Например можно быстро просмотреть ожидающие задачи, чтобы понять причину их блокировки. Можно также свернуть группу, которая не представляет интереса в текущем сеансе отладки. Таким же образом можно группировать задачи по другим столбцам. Можно установить или удалить пометку группы, просто нажав кнопку рядом с заголовком группы. На следующем рисунке показана **задачи** в режиме группирования.  
  
 ![Группированный режим в окне "задачи"](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Представление родительского и дочернего объектов  
 (Данное представление доступно только для управляемого кода.) Щелкните правой кнопкой мыши **состояние** заголовок столбца и выбрав **Group by** > **родительского**, его в иерархическое представление, в котором можно изменить список задач Каждая дочерняя задача представляет собой вложенный узел, который можно отобразить или скрыть под его родительским узлом. 
  
## <a name="flagging-tasks"></a>Пометка задач  
 Можно пометить поток, задача, на котором запущена задача, выбрав задачу элемент списка и затем выбрав **флаг назначенный поток** в контекстном меню или щелкнув значок флага в первом столбце. Если помечается несколько задач, то затем их можно сортировать по столбцу флага, чтобы вывести все помеченные задачи наверх и далее сосредоточиться только на них. Можно также использовать **Параллельные стеки** для просмотра только помеченных задач. Это позволяет отфильтровывать задачи, которые не нужны для отладки. Между сеансами отладки пометки не существуют.  
  
## <a name="freezing-and-thawing-tasks"></a>Замораживание и размораживание задач  
 Можно зафиксировать поток, на котором запущена задача, щелкнув правой кнопкой мыши элемент задачи в списке и выбрав **Заморозить назначенный поток**. (Если задача уже заморожена, команда является **Разморозить назначенный поток**.) Если поток замораживается, то он не будет выполняться при проходе по коду после текущей точки останова. **Заморозить все потоки, но это один** замораживает все потоки, за исключением выполняющего элемент списка задач.
  
 На следующем рисунке показаны остальные пункты меню для каждой задачи.  
  
 ![Контекстное меню потоков в окне задач](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")  

## <a name="switching-the-active-task-or-frame"></a>Выбор активной задачи или кадра

**Переключиться на задачу** команда делает текущей задачи активной задачи. **Перейти к кадру** команда делает стек выбранного фрейма активный кадр стека. Для текущей задачи или кадр стека выбранного переключений контекста отладчика.

## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/debugger-basics.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Параллельное программирование](/dotnet/standard/parallel-programming/index)   
 [Среда выполнения с параллелизмом](/cpp/parallel/concrt/concurrency-runtime)   
 [В окне параллельных стеков](../debugger/using-the-parallel-stacks-window.md)   
 [Пошаговое руководство. Отладка параллельного приложения](../debugger/walkthrough-debugging-a-parallel-application.md)