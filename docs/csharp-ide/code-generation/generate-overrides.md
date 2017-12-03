---
title: "Создать Equals и GetHashCode-метод переопределяет - формирования кода (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Создать Equals и GetHashCode-метод переопределения в C# #

**Что:** позволяет создавать **равняется** и **GetHashCode** методы.

**Когда:** создавать такие переопределения, когда имеется тип, представляющий «значение», которыми должны сравниваться по полям, а не по месту расположения объектов в памяти.

**Почему:** при реализации типа значения, следует рассмотреть возможность переопределения метода Equals с целью улучшения производительности по по умолчанию реализация метода Equals на ValueType.

При реализации ссылочного типа, следует рассмотреть возможность переопределения метода Equals, если ваш тип выглядит как базовый тип, например, точки, строки, BigNumber и т. д.

Переопределите метод GetHashCode, чтобы разрешить тип для правильной работы в хэш-таблице. Продолжите чтение Дополнительные рекомендации [операторы равенства](/dotnet/standard/design-guidelines/equality-operators).

**Как:**

1. Поместите курсор в объявлении типа.

   ![Выделенный код](media/overrides_highlight.png)

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl +.** триггер **Быстрые действия и рефакторинг** и выбрать пункт **создания Equals(object)** или **создания Equals и GetHashCode** из контекстного меню окна предварительного просмотра.
   * **Мышь**
     * Щелкните правой кнопкой мыши и выберите **Быстрые действия и рефакторинг** и выбрать пункт **создания Equals(object)** или **создания Equals и GetHashCode** из окна предварительного просмотра всплывающее окно.
     * Нажмите кнопку ![Лампочки](media/bulb.png) значок, который отображается в левом поле, если текст курсор уже находится в строке с объявлением типа.

   ![Создание предварительного просмотра переопределений](media/overrides_preview.png)

1. Выберите члены, которые вы хотите создавать методы переопределения для:

    ![Создание диалогового окна переопределения](media/overrides_dialog.png)

    > [!TIP]
    > Можно также создавать операторы в этом диалоговом окне с помощью флажков под списком элементов.

1. Equals и GetHashCode переопределения будут созданы с реализации автоматического по умолчанию.

   ![Создания результата метода](media/overrides_result.png)

## <a name="see-also"></a>См. также

[Создание кода (C#)](../code-generation-csharp.md)  
[Просмотр изменений](../../ide/preview-changes.md)