---
title: Указание времени и места применения примечания
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 9d99ebce3adc27039763e11ed4882a20199e8469
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Указание времени и места применения примечания
Если примечание условно, оно может требовать, чтобы другие примечания указали на это анализатору.  Например, если функция имеет переменную, которая может быть либо синхронной, либо асинхронной, то функция ведет себя следующим образом: В синхронном, она всегда завершается успешно, но в случае асинхронного сообщение об ошибке, если он может завершиться сразу. Когда функция вызывается синхронно, проверка значения результата не представляет никакого значения для анализатора кода, поскольку оно не было возвращено.  Однако если функция вызывается асинхронно и результат функции не проверяется, может возникнуть серьезная ошибка. Этот пример иллюстрирует ситуацию, в которой можно использовать примечание `_When_` для включения проверки, как описано далее в этой статье.

## <a name="structural-annotations"></a>Структурные примечания
 Для того, чтобы контролировать, когда и в каких местах применяются примечания, используйте следующие структурные примечания.

|Комментарий|Описание|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` является выражением, которое предоставляет lvalue. Заметки в `anno-list` применяются к объекту с именем `expr`. Для каждого примечания в `anno-list`, `expr` интерпретируется в предусловии, если примечание интерпретируется в предусловии, и в постусловии, если примечание интерпретируется в постусловии.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` является выражением, которое предоставляет lvalue. Заметки в `anno-list` применяются к объекту с именем `expr`. Для каждого примечания в `anno-list`, `expr` интерпретируется в предусловии, если примечание интерпретируется в предусловии, и в постусловии, если примечание интерпретируется в постусловии.<br /><br /> `iter` — имя переменной с областью видимости в примечании (включая `anno-list`). `iter` имеет неявный тип `long`. На основе оценки скрыты одинаковыми именами переменных в любой внешней области видимости.<br /><br /> `elem-count` представляет собой выражение, результатом которого является целым числом.|
|`_Group_(anno-list)`|Примечания в `anno-list` рассматриваются как имеющие любой квалификатор, который применяется к групповому примечанию, применяемому к каждому примечанию.|
|`_When_(expr, anno-list)`|`expr` выражение, которое можно преобразовать в `bool`. Если он не равен нулю (`true`), то примечания, определенные в `anno-list`, считаются применимыми.<br /><br /> По умолчанию для каждого примечания в `anno-list`, `expr` интерпретируется с использованием входных значений, если это примечание с предусловием, и выходных значений, если это примечание с постусловием. Чтобы переопределить настройки по умолчанию, вы можете использовать встроенный `_Old_` для проверки постусловия, чтобы указать, что должны использоваться входные значения. **Примечание:** другие примечания могут быть включены как следствие использования `_When_` Если изменяемое значение — например, `*pLength`— участвует, так как результат вычисления `expr` в предусловии может отличаться от его вычисленное привести в постусловии.|

## <a name="see-also"></a>См. также
 [Использовании аннотаций SAL для сокращения дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [основные сведения о SAL](../code-quality/understanding-sal.md) [Аннотация параметров функции и возвращаемых значений](../code-quality/annotating-function-parameters-and-return-values.md) [Аннотация поведения функций](../code-quality/annotating-function-behavior.md) [Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md) [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md) [встроенные функции](../code-quality/intrinsic-functions.md) [рекомендации и примеры](../code-quality/best-practices-and-examples-sal.md)