---
title: Практическое руководство. Настройка меню и панелей инструментов в Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e9cab18be65d29b6cdd22b8948d2e89f75c4fe9
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745953"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Практическое руководство. Настройка меню и панелей инструментов в Visual Studio

Visual Studio можно настраивать не только путем добавления и удаления панелей инструментов и меню в строке меню, но также путем добавления и удаления команд для любой панели инструментов или любого меню.

> [!WARNING]
> Настроив панель инструментов или меню, убедитесь в том, что ее флажок установлен в диалоговом окне **Настройка**. В противном случае после закрытия и повторного открытия Visual Studio изменения будут утеряны.

## <a name="add-remove-or-move-a-menu-on-the-menu-bar"></a>Добавление, удаление или перемещение меню в строке меню

1.  В строке меню выберите **Сервис** > **Настроить**.

     Откроется диалоговое окно **Настройка**.

2.  На вкладке **Команды** установите переключатель **Строка меню** и флажок **Строка меню** в списке рядом с этим параметром, а затем выполните одно из следующих действий:

    -   Чтобы добавить меню, нажмите кнопку **Добавить новое меню**, нажмите кнопку **Изменить выбор** и введите имя меню, который требуется добавить.

        ![Диалоговое окно "Настройки" с информацией о том, как добавлять меню](../ide/media/addmenu.png)

    -   Чтобы удалить меню, выберите его из списка **Элементы управления** и нажмите кнопку **Удалить**.

    -   Чтобы переместить меню в строке меню, его в списке **Элементы управления**, а затем нажмите кнопку **Вверх** или **Вниз**.

## <a name="add-remove-or-move-a-toolbar"></a>Добавление, удаление или перемещение панели инструментов

1.  В строке меню выберите **Сервис** > **Настроить**.

     Откроется диалоговое окно **Настройка**.

2.  На вкладке **Панель инструментов** выполните одно из следующих действий:

    -   Чтобы добавить панель инструментов, нажмите кнопку **Создать**, укажите имя панели инструментов, которую требуется добавить, а затем нажмите кнопку **ОК**.

        ![Диалоговое окно "Настройки" с информацией о том, как добавлять панель инструментов](../ide/media/addtoolbar.png)

    -   Чтобы удалить пользовательскую панель инструментов, выберите ее из списка **Панели инструментов** и нажмите кнопку **Удалить**.

        > [!IMPORTANT]
        > Удалить можно панели инструментов, созданные пользователем, но не панели инструментов по умолчанию.

    -   Чтобы переместить панель инструментов в другое место закрепления, выберите ее в списке **Панели инструментов**, нажмите кнопку **Изменить выбор**, а затем выберите нужное расположение в отобразившемся списке.

        Можно также перетащить панель инструментов за левый край, чтобы переместить ее в любую точку основной области закрепления.

        > [!NOTE]
        > Дополнительные сведения о повышении практичности и доступности панелей инструментов см. в статье [Практическое руководство. Настройка параметров специальных возможностей в интегрированной среде разработки](../ide/reference/how-to-set-ide-accessibility-options.md).

## <a name="customizing_menu">Настройка меню или панели инструментов</a>

1.  В строке меню выберите **Сервис** > **Настроить**.

    Откроется диалоговое окно **Настройка**.

2.  На вкладке **Команды** выберите переключатель для типа элемента, который необходимо настроить.

3.  В списке для данного типа элементов выберите меню или панель инструментов, которую требуется настроить, а затем выполните одно из нижеуказанных действий.

    -   Чтобы добавить команду, нажмите кнопку **Добавить команду**.

        В диалоговом окне **Добавить команду** выберите элемент в списке **Категории**, выберите элемент в списке **Команды**, а затем нажмите кнопку **ОК**.

        ![Диалоговое окно "Добавить команду" в Visual Studio](../ide/media/addcommand.png)

    -   Чтобы удалить команду, выберите ее из списка **Элементы управления** и нажмите кнопку **Удалить**.

    -   Чтобы изменить порядок расположения команд в списке, выберите команду **Элементы управления**, а затем нажмите кнопку **Вверх** или **Вниз**.

    -   Чтобы сгруппировать команды под горизонтальной линией, выберите первую команду в списке **Элементы управления**, нажмите кнопку **Изменить выбор**, а затем выберите в появившемся меню пункт **Начать группу**.

## <a name="reset-a-menu-or-a-toolbar"></a>Сброс настроек меню или панели инструментов

1.  В строке меню выберите **Сервис** > **Настроить**.

    Откроется диалоговое окно **Настройка**.

2.  На вкладке **Команды** выберите переключатель для типа элемента, параметры которого необходимо сбросить.

3.  В списке для данного типа элементов выберите меню или панель инструментов, параметры которых требуется сбросить.

4.  Нажмите кнопку **Изменить выбор** и выберите пункт **Сброс** в отобразившемся меню.

    Можно также сбросить параметры всех меню и панелей инструментов с помощью кнопки **Сбросить все**.

## <a name="see-also"></a>См. также

- [Персонализация интегрированной среды разработки](../ide/personalizing-the-visual-studio-ide.md)
- [Настройка редактора](../ide/customizing-the-editor.md)