---
title: 'Конструктор рабочих процессов - как: создайте консольное приложение рабочего процесса'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-workflow-console-application"></a>Как создать консольное приложение рабочего процесса

Windows Workflow Foundation (WF) позволяет создавать рабочие процессы для выполнения системных или пользовательских процессов. Конструктор рабочих процессов Windows предоставляет область конструктора для создания таких рабочих процессов. В конструкторе рабочих процессов, которые можно использовать для создания рабочих процессов из среды Visual Studio или его можно интегрировать в другие приложения, где размещается конструктор.

В этом разделе описывается использование конструктора рабочих процессов в Visual Studio 2010 для создания рабочего процесса в консольном приложении.

## <a name="to-create-a-workflow-console-application"></a>Создание приложения командной строки рабочего процесса

1.  Запустите Visual Studio 2010.

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  В **установленные шаблоны** выберите **рабочего процесса** либо из **Visual C#** или **Visual Basic** группирования, в зависимости от вашей язык.

4.  В средней области выберите **консольное приложение рабочего процесса**.

5.  В **имя** введите описательное имя проекта облегчить его определение.

6.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.

7.  В **решения** введите имя для нового решения. Нажмите кнопку **ОК** для создания приложения.

    > [!NOTE]
    > Если вы хотите добавить консольное приложение рабочего процесса в существующее решение, откройте это решение в Visual Studio 2010, щелкните правой кнопкой мыши решение в **обозревателе решений**и выберите **добавить**, затем  **Новый проект** Открытие **новый проект** диалоговое окно. Продолжайте действия, описанные ранее в этой процедуре.

8.  Этот шаблон проекта создает определение рабочего процесса XAML, а также определение приложения командной строки в исходном коде. В конструкторе рабочих процессов открывает и отображает полотно для созданного рабочего процесса.

9. Чтобы составить рабочий процесс, перетащите действия или другие элементы рабочего процесса из **элементов** в область конструктора в рабочем процессе.

## <a name="see-also"></a>См. также

- [Создание проекта рабочего процесса](../workflow-designer/creating-a-workflow-project.md)