---
title: Анализ нарушений правила пороговых значений в нагрузочных тестах в Visual Studio | Документы Майкрософт
ms.date: 10/19/2016
ms.topic: article
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 761d277612242cc4b14b0a24d1a2ac7663b2b152
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Анализ нарушений правила пороговых значений в нагрузочном тесте с помощью анализатора тестовой нагрузки

Правила пороговых значений связаны с определенными счетчиками производительности, их нарушения указывают, что показание счетчика превысило или опустилось ниже установленного значения. При выполнении теста анализируются нарушения предварительно настроенных правил порогового значения.

При возникновении любых нарушений в строке состояния нагрузочного теста появляется гиперссылка **нарушения порогов** и указывается количество обнаруженных нарушений. Эта гиперссылка открывает таблицу нарушений порогового значения. Также для просмотра нарушений используется окно **Счетчики** и диаграмма.

## <a name="view-threshold-violations-in-the-table"></a>Просмотр нарушений порогового значения в таблице

 В таблице нарушений порогового значения отображаются первая тысяча нарушений. Эти столбцы представлены в следующей таблице.

|Столбец|Описание:|Отображается по умолчанию|
|------------|-----------------|------------------------|
|Время|Время возникновения нарушения в нагрузочном тесте.|Да|
|Компьютер|Имя компьютера, на котором произошло нарушение при выполнении теста. **Примечание.** Это важно при выполнении нагрузочного теста на тестовой платформе.|Да|
|Категория|Категория счетчика производительности, в котором произошло нарушение.|Да|
|Счетчик|Имя счетчика производительности, в котором произошло нарушение.|Да|
|Экземпляр|Экземпляр счетчика производительности, в котором произошло нарушение.|Да|
|Сообщение|Сообщение, описывающее нарушение порогового значения. Например, **Значение 5 превышает критическое пороговое значение 0**.|Да|

> [!NOTE]
> Чтобы сортировать таблицу, можно выбирать заголовки столбцов.

 Дополнительные сведения см. в статье [Анализ результатов и ошибок нагрузочного тестирования в представлении таблиц](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Просмотр нарушений порогов на панели счетчиков

 Для просмотра нарушений порогов используется панель **Счетчики**, в которой счетчики производительности для нагрузочного теста представлены в виде дерева. Значки на панели **Счетчики** указывают на серьезность нарушений порогов. Значок будет одним из следующих.

 Значок будет одним из следующих.

 ![Нарушений пороговых значений нет](../test/media/icon_ltest_1.gif "Icon_LTest_1") Нарушений пороговых значений нет.

 ![В последнем интервале произошло нарушение критического порога](../test/media/icon_ltest_2.gif "Icon_LTest_2") В последнем интервале произошло нарушение критического порога.

 ![В предыдущем интервале произошло нарушение критического порога](../test/media/icon_ltest_3.gif "Icon_LTest_3") В предыдущем интервале произошло нарушение критического порога.

 ![В последнем интервале произошло нарушение порога предупреждения](../test/media/icon_ltest_4.gif "Icon_LTest_4") В последнем интервале произошло нарушение порога предупреждения.

 ![В предыдущем интервале произошло нарушение порога предупреждения](../test/media/icon_ltest_5.gif "Icon_LTest_5") В предыдущем интервале произошло нарушение порога предупреждения.

 При необходимости нарушения порогов можно также отображать на диаграмме. Значок порога появляется на диаграмме рядом с точкой данных, в которой произошло нарушение порога.

 В дереве счетчиков действие значка нарушения порогового значения распространяется от указанного узла счетчика до корневого узла. Если дерево не развернуто, нарушение в счетчике может быть невидимо.

 Дополнительные сведения см. в разделе [Использование панели счетчиков в представлении диаграмм и представлении таблиц](../test/counters-panel-in-load-test-analyzer.md).

## <a name="view-threshold-violations-on-the-graph"></a>Просмотр нарушений пороговых значений на диаграмме

 Нарушения пороговых значений можно просмотреть на диаграмме. Значки на диаграмме, аналогично значкам на панели **Счетчики**, обозначают серьезность нарушения порогов. Значки появляются рядом с точкой данных, в которой произошло нарушение порогового значения. Если нарушение произошло в счетчике, которого нет на диаграмме, следует перетащить его туда с панели **Счетчики**.

 Дополнительные сведения см. в статье [Анализ результатов нагрузочного тестирования в представлении диаграмм](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>См. также

- [Указание наборов счетчиков и правил порогов для компьютеров в нагрузочном тесте](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Анализ результатов и ошибок нагрузочного тестирования в представлении таблиц](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)