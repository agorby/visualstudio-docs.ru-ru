---
title: Сбор данных параллелизма для автономных приложений с помощью командной строки профилировщика | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20ae775a6dc49dd2a6dd3cb391eeaf69ff7fa32c
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335948"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Сбор данных параллелизма для автономных приложений с помощью командной строки профилировщика
Метод параллелизма средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] позволяет собирать данные о конфликтах ресурсов и действиях потока, показывающие использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.  
  

## <a name="common-tasks"></a>Типичные задачи  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Запуск приложения платформы .NET Framework и выполнение профилирования данных параллелизма**|-   [Практическое руководство. Запуск приложения .NET Framework для сбора данных параллелизма](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|  
|**Запуск приложения C/C++ и выполнение профилирования данных параллелизма**|-   [Практическое руководство. Запуск собственного приложения для сбора данных параллелизма](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению .NET Framework**|-   [Практическое руководство. Присоединение профилировщика к приложению .NET Framework для сбора данных о параллелизме](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|  
|**Присоединение профилировщика к выполняющемуся приложению C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственному приложению и сбор данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи
  
### <a name="profile-stand-alone-applications"></a>Профилирование автономных приложений  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с помощью метода выборки](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных о взаимодействии уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profile-concurrency-issues"></a>Профилирование проблем параллелизма  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Профилирование приложений ASP.NET**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
|**Профилирование служб**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyze-concurrency-data-views-and-reports"></a>Анализ представлений и отчетов данных параллелизма  
 [Представления данных о конфликтах ресурсов](../profiling/resource-contention-data-views.md)  
  
 [Визуализатор параллелизма](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Ссылка  
 [Справочник по средствам профилирования из командной строки](../profiling/command-line-profiling-tools-reference.md)