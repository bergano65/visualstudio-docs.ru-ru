---
title: "Сбор данных параллелизма для автономных приложений с помощью командной строки профилировщика | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "метод профилирования с параллелизмом"
  - "средства профилирования, метод параллелизма"
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Сбор данных параллелизма для автономных приложений с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Метод параллелизма средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] позволяет собирать данные о конфликтах ресурсов и действиях потока, показывающие использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода\-вывода и другие системные события.  
  
## Общие задачи  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Запуск приложения платформы .NET Framework и выполнение профилирования данных параллелизма**|-   [Практическое руководство. Запуск приложения .NET Framework для сбора данных параллелизма](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Запуск приложения C\/C\+\+ и выполнение профилирования данных параллелизма**|-   [Практическое руководство. Запуск собственного приложения для сбора данных параллелизма](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению .NET Framework**|-   [Практическое руководство. Присоединение профилировщика к приложению .NET Framework для сбора данных о параллелизме](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению C\/C\+\+**|-   [Практическое руководство. Присоединение профилировщика к собственному приложению и сбор данных параллелизма](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)|  
  
## Связанные задачи  
  
### Профилирование автономных приложений  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование с помощью метода выборки**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### Проблемы профилирования параллелизма  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование приложений ASP.NET**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Профилирование служб**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### Анализ представлений и отчетов данных параллелизма  
 [Представления данных о конфликтах ресурсов](../profiling/resource-contention-data-views.md)  
  
 [Визуализатор параллелизма](../profiling/concurrency-visualizer.md)  
  
## Справочные сведения  
 [Справочник по средствам профилирования из командной строки](../profiling/command-line-profiling-tools-reference.md)