---
title: 'CA2143: прозрачные методы не должны использовать требования безопасности'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6e4bad795ccf89b36d4fc6a12b29ba4ada7fbb9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: прозрачные методы не должны использовать требования безопасности
|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Tranparent тип или метод декларативно помечается <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` запросу или вызовы методов <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> метод.

## <a name="rule-description"></a>Описание правила
 Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Прозрачный для системы безопасности код должен использовать полные требования для принятия решений по безопасности, и критичный в плане безопасности код не должен полагаться на прозрачный код, чтобы создать полное требование. Вместо этого следует критичный в плане безопасности любой код, который выполняет проверки безопасности, такие как требования безопасности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Как правило, чтобы устранить нарушение данного правила, пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибута. Можно также удалить требование.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Это правило срабатывает на следующий код, поскольку прозрачный метод создает требование декларативной безопасности.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>См. также
 [CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)