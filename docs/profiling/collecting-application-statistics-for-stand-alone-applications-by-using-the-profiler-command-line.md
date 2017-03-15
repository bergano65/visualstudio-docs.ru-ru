---
title: "Сбор статистики по автономным приложениям с помощью командной строки профилировщика | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "метод профилирования с выборкой"
  - "средства профилирования, метод выборки"
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Сбор статистики по автономным приложениям с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описаны процедуры и параметры для сбора статистики производительности клиентского \(автономного\) приложения с использованием метода выборки в командной строке.  
  
> [!NOTE]
>  Функции усиленной безопасности в Windows 8 и Windows Server 2012 требуют значительных изменений в способе сбора данных профилировщиком Visual Studio на этих платформах.  Для Приложений Магазина Windows также требуются новые методы сбора.  См. раздел [Профилирование приложений для Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Общие задачи  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Запуск приложения с использованием профилировщика**|-   [Практическое руководство. Запуск автономного приложения и сбор статистики приложения](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению .NET Framework**|-   [Практическое руководство. Присоединение профилировщика к приложению .NET Framework для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Присоединение профилировщика к выполняющемуся приложению C\/C\+\+**|-   [Практическое руководство. Присоединение профилировщика к собственному приложению и сбор статистики приложения](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Связанные задачи  
  
### Профилирование автономных приложений  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Инструментирование приложения**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Сбор данных о выделении памяти .NET и сборке мусора**|-   [Сбор данных об использовании памяти .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Сбор данных о конфликтах ресурсов и выполнении потоков**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### Профилирование с помощью метода выборки  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование веб\-приложений ASP.NET**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Профилирование служб**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md).  Содержит описание сбора статистики производительности служб Windows с помощью метода выборки.|  
  
### Анализ представлений и отчетов данных выборки  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)