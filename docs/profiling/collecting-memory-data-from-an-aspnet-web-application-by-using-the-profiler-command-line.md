---
title: "Сбор данных об использовании памяти для веб-приложений ASP.NET с помощью командной строки профилировщика | Microsoft Docs"
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
  - "метод профилирования памяти .NET"
  - "средства профилирования, метод памяти .NET"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Сбор данных об использовании памяти для веб-приложений ASP.NET с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описаны процедуры и параметры сбора данных о выделении памяти и времени существования объектов для веб\-приложения ASP.NET с помощью средства командной строки **VSPerfCmd**.  
  
> [!NOTE]
>  Средство **VSPerfCmd** предоставляет полный доступ к функциональности средств профилирования, включая остановку и возобновление профилирования и сбор дополнительных сведений счетчиков производительности Windows и процессора.  Можно также воспользоваться средством командной строки **VSPerfASPNETCmd**, если эта функциональность не нужна.  В отличие от средства командной строки [VSPerfCmd](../profiling/vsperfcmd.md), нет необходимости устанавливать переменные окружения и перезагружать компьютер.  Для получения дополнительной информации см. [Быстрое профилирование веб\-сайтов с помощью средства VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Общие задачи  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Присоединение профилировщика к выполняющемуся приложению ASP.NET**|-   [Практическое руководство. Присоединение профилировщика к веб\-приложению ASP.NET для сбора данных об использовании памяти](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Инструментирование статически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование статически скомпилированного приложения ASP.NET и сбор данных об использовании памяти](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Инструментирование динамически скомпилированных двоичных файлов**|-   [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор данных об использовании памяти](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## Связанные задачи  
  
### Профилирование веб\-приложений ASP.NET  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование с помощью метода выборки**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Профилирование данных об использовании памяти .NET Framework  
  
|Задача|Связанное содержимое|  
|------------|--------------------------|  
|**Профилирование автономных \(клиентских\) приложений**|-   [Сбор данных об использовании памяти .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Профилирование служб**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Анализ представлений и отчетов по данным об использовании памяти .NET  
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)  
  
## Справочные сведения  
 [Справочник по средствам профилирования из командной строки](../profiling/command-line-profiling-tools-reference.md)