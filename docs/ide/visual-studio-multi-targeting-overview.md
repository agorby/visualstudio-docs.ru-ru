---
title: Нацеливание на платформу .NET Framework в Visual Studio
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cba93b86d6ecebf249e11d18bd6e4b6b86e59fda
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="visual-studio-multi-targeting-overview"></a>Обзор настройки для различных версий в Visual Studio

В Visual Studio можно указать версию или профиль платформы .NET Framework, которая будет предназначена для проекта. Для запуска приложения на другом компьютере версия платформы для приложения должна быть совместима с версией платформы, установленной на компьютере.

Можно также создать решение, содержащее проекты, ориентированные на разные версии платформы. Нацеливание на платформу помогает гарантировать, что приложение использует только те функциональные возможности, которые доступны в указанной версии платформы.

> [!TIP]
> Вы также можете нацеливать приложения на различные платформы. Дополнительные сведения см. в разделе [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Функции нацеливания на платформу

Среди прочего, доступны следующие возможности нацеливания на платформу:

- При открытии проекта, который ориентирован на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio может автоматически обновить его или оставить имеющуюся настройку.

- При создании проекта можно указать версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую требуется ориентироваться.

- Можно изменить версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую ориентирован существующий проект.

- В каждом из нескольких проектов в одном решении можно ориентироваться на разные версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

- При изменении версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую сориентирован проект, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] вносит все необходимые изменения в ссылки и файлы конфигурации.

При работе над проектом, нацеленным на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio динамически изменяет среду разработки, как показано ниже:

- Фильтрует элементы в диалоговых окнах **Добавить новый элемент**, **Добавить новую ссылку** и **Добавление ссылки на службу**, чтобы пропустить варианты, которые недоступны в целевой версии.

- Фильтрует пользовательские элементы управления на **панели элементов**, чтобы удалить те из них, которые недоступны в целевой версии, и отобразить только наиболее актуальные элементы, если доступно несколько элементов управления.

- Фильтрует **IntelliSense**, чтобы пропустить языковые функции, которые недоступны в целевой версии.

- Фильтрует свойства в окне **Свойства**, чтобы пропустить те, которые недоступны в целевой версии.

- Фильтрует пункты меню, чтобы пропустить те, которые не доступны в целевой версии.

- Для сборок система использует версию и параметры компилятора, которые подходят для целевой версии.

> [!NOTE]
> Нацеливание на платформу не гарантирует правильную работу приложения. Нужно протестировать приложение, чтобы убедиться в том, что оно работает с целевой версией. Нельзя выбрать в качестве целевых версий платформы, предшествующие .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Выбор целевой версии платформы

При создании проекта выберите целевую версию .NET Framework в диалоговом окне **Новый проект**. Список доступных платформ включает их установленные версии, соответствующие типу выбранного шаблона. Для типов шаблонов, которые не требуют .NET Framework, например шаблонов .NET Core, раскрывающийся список **Framework** скрыт.

![Раскрывающийся список Framework в диалоговом окне "Новый проект"](media/vside-newproject-framework.png)

Для существующего проекта можно изменить целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в диалоговом окне свойств проекта. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Разрешение системных ссылок и пользовательских ссылок на сборки

Чтобы нацелиться на определенную версию .NET Framework, нужно сначала установить подходящие ссылки на сборки. Вы можете скачать пакеты разработчика для разных версий .NET Framework на странице [файлов для загрузки .NET](https://www.microsoft.com/net/download/windows).

Диалоговое окно **Добавить ссылку** позволяет отключить системные сборки, не относящиеся к целевой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], чтобы их нельзя было добавить в проект случайно. (Системные сборки — это файлы *.dll*, включенные в версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].) Ссылки, которые относятся к версии платформы, которая старше целевой версии, не будут разрешены, а зависящие от них элементы управления невозможно будет добавить. Если вы хотите активировать такую ссылку, измените целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] для проекта на ту, которая содержит эту ссылку.  Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Дополнительные сведения о ссылках на сборки см. в разделе [Разрешение сборок во время разработки](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Включение LINQ

При нацеливании на .NET Framework 3.5 или более поздней версии ссылка на **System.Core** и импорт уровня проекта для <xref:System.Linq> (только в Visual Basic) добавляются автоматически. Если вы хотите использовать функции LINQ, нужно также включить параметр `Option Infer` (только в Visual Basic). Ссылка и импорт удаляются автоматически при изменении целевой версии на более раннюю версию .NET Framework. Дополнительные сведения см. в разделе [Работа с LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>См. также

- [Настройка для различных версий (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)