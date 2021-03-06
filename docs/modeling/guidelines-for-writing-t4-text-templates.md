---
title: Рекомендации по написанию текстовых шаблонов T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f96cea682699382b55b786001a175616c877804a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Рекомендации по написанию текстовых шаблонов T4
Эти общие рекомендации могут быть полезны при создании программного кода или других ресурсов приложения в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Они не являются фиксированными правила.

## <a name="guidelines-for-design-time-t4-templates"></a>Рекомендации для шаблонов времени разработки T4
 Шаблоны T4 времени разработки — это шаблоны, создание кода в ваш [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта во время разработки. Дополнительные сведения см. в разделе [создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Создавайте переменные аспекты приложения.
Создание кода наиболее полезно для тех аспектов приложения, могут измениться во время проекта или будут изменяться между разными версиями приложения. Отделите эти переменные аспекты от относительно неизменных аспектов, чтобы вы легко определить, что должен создаваться. Например если приложение предоставляет веб-сайт, различные стандартные функции предоставления страниц от логики, определяющей пути перехода от одной страницы в другую.

 Напишите код переменных аспектов в одной или нескольких моделей источника.
Модель — это файл или база данных, считываемые шаблонами для получения определенных значений для переменных частей кода, который будет создан. Модели могут быть базами данных, XML-файлы разработки, схемы или доменных языков. Как правило, одна модель используется для создания многих файлов в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта. Каждый файл создается отдельный шаблон.

 В проекте можно использовать более одной модели. Например можно определить модель для перехода между веб-страницы и отдельная модель для разметки страниц.

 Фокусировки модели потребности пользователей и словарь, отличный от реализации.
Например в приложении веб-сайта предполагается модель для ссылки на веб-страницы и гиперссылки.

 В идеальном случае выберите форму, наиболее подходящий тип информации, который представляет модель представления. Например модель путей перехода по веб-сайт может быть диаграмма прямоугольников и стрелок.

 Тестирование созданного кода.
Позволяет убедиться, что получившийся код работает как нужно пользователям ручные или автоматические тесты. Не следует создавать тесты из той же модели, из которого создается код.

 В некоторых случаях общие тесты могут выполняться на модели напрямую. Например можно написать тест, который гарантирует, что каждой странице на веб-узле можно осуществлять путем переходов с любой другой.

 Разрешение пользовательского кода: создание разделяемых классов.
Разрешить для создаваемого кода вручную в дополнение к автоматически создаваемому коду. Он является обычным для схеме создания кода иметь возможность учетной записи для всех возможных вариантов, которые могут возникнуть. Таким образом следует ожидать добавить или переопределить некоторые из созданного кода. Где автоматически создаваемый материал — на языке .NET, таких как [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], особенно полезны две стратегии:

-   Созданные классы должны быть разделяемыми. Это дает возможность для добавления содержимого в созданном коде.

-   Классы должны создаваться парами, один наследование от другого. Базовый класс должен содержать все созданные методы и свойства, и производный класс должен содержать только конструкторы. Это позволяет коду рукописный переопределять любые созданные методы.

 В других языках созданный, например XML, используйте `<#@include#>` директива с легкостью объединять рукописный и созданного содержимого. В более сложных случаях может потребоваться выполнить запись на этапе после обработки, объединяющий автоматически созданный файл с файлами, написанными вручную.

 Перемещение общего материала в включаемых файлов или шаблонов во время выполнения, чтобы избежать повторения похожих блоков текста и кода в нескольких шаблонах используйте `<#@ include #>` директивы. Дополнительные сведения см. в разделе [директива Include T4](../modeling/t4-include-directive.md).

 Можно также создавать шаблоны текста во время выполнения в отдельном проекте и затем вызывать их из шаблона времени разработки. Чтобы сделать это, используйте `<#@ assembly #>` директиву, чтобы получить доступ к отдельному проекту. Примеры см. в разделе [«Наследования в текстовые шаблоны» в блоге Джонс Гарета](http://go.microsoft.com/fwlink/?LinkId=208373).

 Перенесите большие блоки кода в отдельную сборку.
 Если у вас есть большие блоки и блоки возможностей класса, можно переместить некоторые из этого кода в методы, которые компилируются в отдельном проекте. Можно использовать `<#@ assembly #>` директивы для доступа к коду в шаблоне. Дополнительные сведения см. в разделе [директива Assembly T4](../modeling/t4-assembly-directive.md).

 Методы можно поместить в абстрактный класс, который может наследовать шаблона. Абстрактный класс должен наследоваться от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Дополнительные сведения см. в разделе [директива Template T4](../modeling/t4-template-directive.md).

 Создание кода, не конфигурации файлы одним из способов написания изменяющегося приложения заключается в написании универсального программного кода, который принимает файл конфигурации. Приложения, написанного таким образом стал более гибким и можно изменить при изменении потребностей бизнеса без повторного построения приложения. Недостаток данного подхода то, что приложение будет работать хуже, чем более конкретного приложения. Кроме того его программный код будет более сложным для понимания и обслуживания, частично, так как она должна всегда работать с более универсальными типами.

 В отличие от этого, переменные части которого автоматически создаются до компиляции приложения может быть строго типизированным. Это позволяет намного проще и надежнее писать код вручную и интегрировать его с автоматически создаваемыми частями программного обеспечения.

 Чтобы получить максимальную выгоду от создания кода, попробуйте создавать программный код, а не файлы конфигурации.

 Используйте папку кода, созданного Поместите шаблоны и созданные файлы в проект папку с именем **кода, созданного**, чтобы сделать его очистки, что эти файлы не следует редактировать непосредственно. При создании пользовательского кода, чтобы переопределить или добавить созданные классы, поместите эти классы в папку с именем **пользовательский код**. Структура типичного проекта выглядит следующим образом:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs

```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Рекомендации для шаблонов времени выполнения (предварительно обработанном) T4
 Перемещение общего материала в наследуемые шаблоны можно использовать наследование для совместного использования методов и блоков текста между текстовых шаблонов T4. Дополнительные сведения см. в разделе [директива Template T4](../modeling/t4-template-directive.md).

 Можно также использовать файлы включения с шаблонами времени выполнения.

 Перемещение крупных фрагментов кода в разделяемый класс.
Каждый шаблон времени выполнения создает определение разделяемого класса, который имеет то же имя, что и шаблон. Можно создать файл кода, содержащий другом частичном определении того же класса. Класс таким образом, можно добавить методы, поля и конструкторы. Эти элементы могут вызываться из блоков кода в шаблоне.

 Преимущество такого подхода является код проще, так как технология IntelliSense доступна. Кроме того можно добиться лучшего разделения между презентации и базовую логику.

 Например, в **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 В **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 Разрешение пользовательского кода: предоставление точек расширения, рассмотрите возможность создания виртуальных методов в \<#+ класса будут заблокированы #>. Это позволяет один шаблон для использования во множестве контекстов, без изменений. Вместо изменения шаблона, можно создать производный класс, предоставляющий минимальную дополнительную логику. Производный класс может быть либо обычный код или он может быть шаблоном во время выполнения.

 Например в MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 В коде приложения:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();

```

## <a name="guidelines-for-all-t4-templates"></a>Рекомендации для всех шаблонов T4
 Отдельные сбора данных от создания текста не рекомендуется смешивать вычисления и блоки текста. В каждом текстовом шаблоне используйте первый \<блок кода #, #> для задания переменных и выполнения сложных вычислений. Из первого блока текст вниз до конца шаблона, либо первый \<# блока функции класса #+ >, избегайте длинных выражений и избежать циклов и условий, если они не содержат текстовые блоки. Такой подход делает шаблон упрощает чтение и обслуживание.

 Не используйте `.tt` для включаемых файлов использовать другое расширение файла, например `.ttinclude` для включаемых файлов. Используйте `.tt` только для файлов, которые должны быть обработаны либо как во время выполнения или во время разработки текстовые шаблоны. В некоторых случаях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] распознает `.tt` файлы и автоматически устанавливает их свойства для обработки.

 Начинайте каждый шаблон с фиксированного прототипа.
Напишите пример кода или текста, который вы хотите создать и убедитесь в том, что он работает. Затем измените его расширение на tt и постепенно вставлять код, который изменяет содержимое, считывая модель.

 Рассмотрите возможность использования типизированных моделей.
Несмотря на то, что можно создать схему XML или базы данных для моделей, может оказаться полезным создать доменный язык (DSL). Доменный язык DSL имеет то преимущество, что он создает класс для представления каждого узла в схеме и свойств для представления атрибутов. Это означает, что вы можете программировать с точки зрения бизнес-модели. Пример:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Рассмотрите возможность использования схем для моделей.
Многие модели представлены наиболее эффективно и управляемых виде текстовых таблиц, особенно в том случае, если они имеют очень большой размер.

 Однако для некоторых видов бизнес-требований важно пояснить сложные наборы связей и рабочих процессов и схемы являются наилучшим образом подходит средний. Преимуществом схемы является его легко обсуждать с пользователями и другими заинтересованными лицами. Создание кода из модели на уровне бизнес-требований, можно сделать код более гибким при изменении требований.

 Также можно создать свой собственный тип диаграммы как доменный язык (DSL). Код может быть создан из UML и DSL. Дополнительные сведения см. в разделе [анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>См. также

- [Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
