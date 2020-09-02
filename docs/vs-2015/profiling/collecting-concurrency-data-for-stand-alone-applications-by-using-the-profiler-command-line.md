---
title: Сбор данных параллелизма для автономных приложений с помощью командной строки профилировщика | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fac1c840d93c03b659e7934a82eb53895b60ede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141932"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Сбор данных параллелизма для автономных приложений с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Метод параллелизма средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет собирать данные о конфликтах ресурсов и действиях потока, показывающие использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Запуск приложения платформы .NET Framework и выполнение профилирования данных параллелизма**|-   [Как запустить приложение .NET Framework для получения данных о параллелизме](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Запуск приложения C/C++ и выполнение профилирования данных параллелизма**|-   [Практическое руководство. Запуск собственного приложения для сбора данных параллелизма](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению .NET Framework**|-   [Практическое руководство. Присоединение профилировщика к приложению .NET Framework для сбора данных о параллелизме](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственному приложению и сбор данных параллелизма](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-stand-alone-applications"></a>Профилирование автономных приложений  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с использованием выборки](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных .NET Framework памяти](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных об уровневом взаимодействии](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Профилирование проблем параллелизма  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Профилирование приложений ASP.NET**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Профилирование служб**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Анализ представлений и отчетов данных параллелизма  
 [Представления данных о состязаниях за ресурсы](../profiling/resource-contention-data-views.md)  
  
 [Визуализатор параллелизма](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Ссылка  
 [Справочник по Средства профилирования командной строки](../profiling/command-line-profiling-tools-reference.md)
