---
title: Конструктор рабочих процессов - ForEach&lt;T&gt; конструктора действий
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d506be0fbee9ad94e4ed8b97665665bc045ed130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; конструктора действий

Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> свойств в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ForEach%601.Values%2A>, введите выражение Visual Basic в **значения** поле на **ForEach < T\>**  действия конструктора или в сетке свойств.|
|*TypeArgument*|Да|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, указанное в универсальном параметре *T*. По умолчанию *TypeArgument* равно **Int32**. Чтобы изменить тип, измените значение *TypeArgument* поле со списком в сетке свойств.|

По умолчанию именем итератора цикла является **элемент**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>См. также

- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)